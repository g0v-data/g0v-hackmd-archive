# Chapter 13 — Graph Neural Networks

> **Course:** Deep Learning  **Class code:** DL — Ch 13   **Lecturer:** —
> **Primary textbook:** Bishop & Bishop, *Deep Learning: Foundations and Concepts* (Springer, 2024), Ch 13
> **Translation:** Traditional Chinese (Taiwan)  ·  圖神經網路

---

## Section 1 — Learning Objectives

### Today's Goals

- Define what makes data **graph-structured** and identify the three task families on graphs.
- Build the **adjacency matrix** of a graph and explain why a graph network must be **permutation-equivariant**.
- Derive the **Aggregate + Update** template from a CNN filter; recognise it as the source of permutation equivariance.
- Pick an aggregation operator (sum, mean, symmetric-norm, max, MLP) appropriate for a task.
- Read **Algorithm 13.1** (node-only message passing) and **Algorithm 13.2** (nodes + edges + graph embedding).
- Explain **over-smoothing** and the two main remedies (residuals, multi-layer readout).
- State the place of GNNs inside **geometric deep learning** as equivariance with respect to a symmetry group.

### Before We Start

> **Motivating Question — 1.** A spam-detection model is trained on individual emails. Now the security team gives you the *graph* of who emails whom and you must classify users, not emails. Why can a plain MLP not be used here, and what mathematical property must the new model satisfy?

> **Motivating Question — 2.** A molecule has the same chemistry however its atoms happen to be numbered in a file. What must a learned function of the molecule *not* depend on?

> **Key Concept — Equivariance under relabelling (對置換的等變性).** A graph has no canonical ordering of its nodes. A graph network's output must therefore behave predictably when the inputs are relabelled — for node-level outputs the labels must permute in the same way as the inputs (equivariance), for whole-graph outputs the result must not change at all (invariance).

---

## Section 2 — Key Definitions

| Term | Definition | 中文 |
| --- | --- | --- |
| Graph                       | A pair G = (V, E) of nodes V and edges E ⊆ V × V.                                              | 圖 |
| Node / Vertex               | An entity in the graph; carries an embedding $h_n \in \mathbb{R}^D$.                            | 節點 |
| Edge                        | A connection between two nodes; may carry an embedding $e_{nm}$.                                | 邊 |
| Neighbourhood $N(n)$        | The set of nodes connected to node $n$ by an edge.                                              | 鄰居集合 |
| Degree                      | $|N(n)|$, the number of neighbours of node $n$.                                                 | 度數 |
| Adjacency matrix $A$        | $N \times N$ matrix with $A_{nm}=1$ if $(n,m)\in E$, else 0.                                    | 鄰接矩陣 |
| Undirected graph            | $A = A^\top$.                                                                                    | 無向圖 |
| Directed graph              | Edges are ordered pairs; $A$ need not be symmetric.                                              | 有向圖 |
| Self-loop                   | An edge from $n$ to $n$; appears as a 1 on the diagonal of $A$.                                  | 自迴圈 |
| Permutation matrix $P$      | A 0/1 matrix with exactly one 1 per row and per column.                                          | 置換矩陣 |
| Invariant function $f(X)$   | $f(PX) = f(X)$ for every permutation $P$.                                                        | 不變函數 |
| Equivariant function $f(X)$ | $f(PX) = P f(X)$ for every permutation $P$.                                                      | 等變函數 |
| Aggregate                   | A permutation-invariant function that pools messages from $N(n)$ into one vector $z_n$.          | 彙整 |
| Update                      | A learnable function that combines $h_n$ with $z_n$ to give $h_n^{(l+1)}$.                       | 更新 |
| Message-passing layer       | One Aggregate-then-Update step applied in parallel to every node.                                | 訊息傳遞層 |
| Receptive field             | The set of nodes that can influence a target node after $L$ layers — all nodes within $L$ hops. | 感受野 |
| Readout                     | The head that turns final node embeddings into a node-, edge- or graph-level prediction.        | 讀出函數 |
| Over-smoothing              | Loss of discriminative information as embeddings drift together with depth.                      | 過度平滑 |
| Inductive setting           | Train on some graphs, test on entirely new graphs.                                               | 歸納式學習 |
| Transductive setting        | Whole graph is known; predict labels of its unlabelled nodes.                                    | 直推式學習 |

---

## Section 3 — Main Results · Why It Matters

| Result | Statement | Why It Matters |
| --- | --- | --- |
| Adjacency under relabelling          | If nodes are permuted by $P$, then $A \mapsto P A P^\top$ (Eq 13.3). | The matrix changes but the graph does not — explains why models must be permutation-equivariant. |
| Equivariance preservation under sums | $\sum$ of permutation-equivariant maps is permutation-equivariant. | Justifies stacking message-passing layers without breaking the symmetry. |
| CNN-filter ⇒ graph convolution       | Replacing per-position weights $w_j$ by one shared weight $w_{\text{neigh}}$ over the neighbour sum (Eqs 13.8 → 13.9). | Shows the Aggregate + Update template is *not* a heuristic — it is what is left after enforcing permutation invariance. |
| Sum aggregation is universal         | Any permutation-invariant function of a multiset can be written as $\rho(\sum_m \phi(h_m))$ (Deep Sets, Zaheer 2017). | Justifies MLP aggregators (Eq 13.15); a graph with no edges reduces to Deep Sets. |
| Receptive field grows by one per layer | After $L$ layers, node $n$ depends on all nodes within $L$ hops. | Sets the depth needed to reach the whole graph; also drives over-smoothing. |
| GAT special case ⇒ Transformer        | A fully-connected graph with multi-head attention is exactly the Transformer encoder. | Unifies GNN, attention, and Transformer architectures (Exercise 13.9). |

---

## Section 4 — Main Teaching Flow

---

### 13.1 · Machine learning on graphs

#### Graph-structured data is everywhere

**Focus.** Many objects are sets of entities related by edges, not vectors in $\mathbb{R}^D$.

- A **molecule (分子)**: atoms are nodes, bonds are edges, atom types and bond orders are features.
- A **transport network (運輸網路)**: stations are nodes, tracks are edges, capacities and timings are features.
- **The web / social networks (網路與社群網路)**: pages or users are nodes, hyperlinks or friendships are edges.

![Example_GraphStructure](https://g0v.hackmd.io/_uploads/HylOO0KxlGg.png =300%x)

> **Why This Matters.** Replacing a plain feature vector by a graph means the model must respect two structural facts: variable input size, and absence of a canonical node ordering.

#### Three task families on graphs

| Task | Output | Example |
| --- | --- | --- |
| **Node prediction (節點預測)**  | One label per node          | Classify documents in a citation network. |
| **Edge prediction (邊預測 / 圖補全)** | A score for each candidate edge | Predict a missing protein interaction. |
| **Graph prediction (圖預測)** | One label for the whole graph | Is this molecule toxic? |

> **Pattern to Notice.** Node and edge tasks need **equivariant** outputs; graph tasks need **invariant** outputs. The readout (Section 13.2) is what changes; the message-passing backbone is the same.

> **Pause and Ask.** Which of *inductive* and *transductive* matches each task above? Is a molecule classifier inductive or transductive?

---

#### 13.1.1 · Graph properties

**Focus.** Fix vocabulary on the running example.

**Running example.** Five nodes $\{A, B, C, D, E\}$ with edges $\{(A,B), (A,C), (B,C), (B,D), (C,E)\}$.

- Degrees: $|N(A)| = 2$, $|N(B)| = 3$, $|N(C)| = 3$, $|N(D)| = 1$, $|N(E)| = 1$.
- The graph is **simple** — no self-loops, no multi-edges.
- **Connected (連通) :** every pair of nodes is joined by some path.

> **Visual Hint.** Draw the graph with $B$ and $C$ as the two high-degree "hubs" in the middle; $D$ and $E$ are the leaves; $A$ bridges $B$ and $C$.

---

#### 13.1.2 · Adjacency matrices

**Focus.** A graph $\Leftrightarrow$ a matrix, but the matrix is only defined *up to relabelling*.

> **Important Formula.**
> $$A \in \{0,1\}^{N\times N}, \qquad A_{nm}=1 \iff (n,m) \in E. \tag{13.1}$$
> Undirected graphs satisfy $A = A^\top$.

![Adjacenty_order2](https://g0v.hackmd.io/_uploads/HyxRCKexfe.png =300%x)


**Example — adjacency under two orderings.** For the running 5-node example:

Order $A, B, C, D, E$:
$$A = \begin{pmatrix} 0&1&1&0&0\\ 1&0&1&1&0\\ 1&1&0&0&1\\ 0&1&0&0&0\\ 0&0&1&0&0 \end{pmatrix}$$

Order $C, E, A, D, B$:
$$A' = \begin{pmatrix} 0&1&1&0&1\\ 1&0&0&0&0\\ 1&0&0&0&1\\ 0&0&0&0&1\\ 1&0&1&1&0 \end{pmatrix}$$

> **Common Mistake.** Treating $A$ as the "ground truth" representation. Different orderings give different matrices but the *same graph*.

---

#### 13.1.3 · Permutation equivariance

**Focus.** Make the relabelling action precise.

> **Important Formula — permutation matrix (置換矩陣).** $P \in \{0,1\}^{N \times N}$ with exactly one 1 per row and column. Concretely, for the relabelling $(A,B,C,D,E)\to(C,E,A,D,B)$ above:
> $$P = \begin{pmatrix} 0&0&1&0&0\\ 0&0&0&0&1\\ 1&0&0&0&0\\ 0&0&0&1&0\\ 0&1&0&0&0 \end{pmatrix}$$

**Action on a feature matrix.** Stack node features as $X \in \mathbb{R}^{N \times D}$ (row $n$ = features of node $n$). Relabelling gives $\tilde X = P X$.

**Action on the adjacency matrix.**
$$\tilde A = P A P^\top. \tag{13.3}$$

> **Setup → Proof → Conclusion — Eq 13.3.**
> **Setup.** Under permutation $\pi$ with matrix $P$, node $n$ in the new ordering corresponds to node $\pi^{-1}(n)$ in the old ordering. So $\tilde A_{nm} = A_{\pi^{-1}(n), \pi^{-1}(m)}$.
> **Proof.** $(P A P^\top)_{nm} = \sum_{i,j} P_{ni} A_{ij} P_{mj} = A_{\pi^{-1}(n), \pi^{-1}(m)}$ since each row of $P$ has a single 1.
> **Conclusion.** Hence $\tilde A = P A P^\top$.
> **Takeaway.** $A$ and $PAP^\top$ describe the same graph; any graph function we build must therefore be invariant under $A \mapsto PAP^\top$.

> **Important Formula — Invariance vs Equivariance.**
> *Invariant (不變) :* $f(PX, PAP^\top) = f(X, A)$ — for graph-level outputs.
> *Equivariant (等變) :* $F(PX, PAP^\top) = P\,F(X, A)$ — for node-level outputs.

> **Pause and Ask.** Why is invariance not "stronger" than equivariance? Could we just enforce invariance everywhere?
> (*Hint: we still need to know **which** node received which prediction.*)

---

### 13.2 · Neural message passing

---

#### 13.2.1 · A CNN filter is already a graph computation

**Focus.** Derive graph convolution by *removing* the position dependence of a CNN filter.

![CNN4Graph](https://g0v.hackmd.io/_uploads/HJswl5eeMl.png =300%x)


A standard 2-D CNN filter centred at pixel $i$ sums neighbours $j \in N(i)$ with **per-position** weights:
$$z_i^{(l+1)} = f\!\left( \sum_{j \in N(i)} w_j\, z_j^{(l)} + b\right). \tag{13.8}$$

Switch to an *un-ordered* grid: there is no notion of "the top-left neighbour", so $w_j$ cannot depend on the slot $j$. The only choice that does not depend on a node's position is one shared weight for every neighbour, plus a separate self-weight:
$$z_i^{(l+1)} = f\!\left( w_{\text{neigh}} \sum_{j \in N(i)} z_j^{(l)} + w_{\text{self}}\, z_i^{(l)} + b \right). \tag{13.9}$$

> **Key Idea.** The CNN filter *is* a tiny GNN — once we drop position labels, "permutation invariant" is forced on us.

> **Why This Matters.** Equation 13.9 is the simplest graph convolution. Everything that follows in §13.2–§13.3 generalises 13.9.

---

#### 13.2.2 · Aggregate + Update — the template

**Focus.** Split each layer into a permutation-invariant *Aggregate* step followed by a learnable *Update* step.

> **Important Formula — Aggregate / Update layer.**
> $$z_n^{(l)} = \mathrm{Aggregate}\bigl\{ h_m^{(l)} : m \in N(n) \bigr\}, \tag{13.10}$$
> $$h_n^{(l+1)} = \mathrm{Update}\bigl( h_n^{(l)},\, z_n^{(l)} \bigr). \tag{13.11}$$

Initial embeddings: $h_n^{(0)} = x_n$. Apply Aggregate then Update **in parallel for every node**. Each repetition is one **message-passing layer (訊息傳遞層)**.

**Terminology — Message-passing neural network (訊息傳遞神經網路).** A unifying name for graph models built from this two-step pattern (Gilmer et al., 2017). Parameters may be independent per layer, or shared across layers.

> **Pause and Ask.** Why must `Aggregate` be permutation-invariant *as a function of its set argument*, but `Update` need not be?

---

#### Algorithm 13.1 · Simple message-passing

![Algorithm1](https://g0v.hackmd.io/_uploads/HyPox9gxfx.png =300%x)



> **Focus.** All nodes update in parallel, with the **same parameters** $W^{(l)}$ — this is the source of permutation equivariance.

> **Pause and Ask.** After $L$ layers, how far through the graph has information from a single starting node travelled?
> (*Answer: $L$ hops — node $n$ sees its $L$-hop neighbourhood. This is the **receptive field**.*)

---

#### 13.2.3 · Aggregation operators

**Focus.** Several legitimate choices; they differ in expressive power and parameter count.

![Aggregation](https://g0v.hackmd.io/_uploads/ryrfb9elMe.png =300%x)


> **Important Formulas.**
>
> **Sum (求和) :** $\quad z_n = \sum_{m \in N(n)} h_m^{(l)} \tag{13.12}$
> No parameters. Output magnitude grows with degree — helpful when degree is informative, harmful otherwise.
>
> **Mean (平均) :** $\quad z_n = \tfrac{1}{|N(n)|} \sum_{m \in N(n)} h_m^{(l)} \tag{13.13}$
> Normalises by degree. Hides degree information.
>
> **Symmetric normalisation (對稱歸一化, Kipf & Welling) :** $\quad z_n = \sum_{m \in N(n)} \dfrac{h_m^{(l)}}{\sqrt{|N(n)|\,|N(m)|}} \tag{13.14}$
> Down-weights high-degree neighbours; standard in **GCN**.
>
> **Element-wise max / min :** $\quad z_n = \max_{m \in N(n)} h_m^{(l)} \quad (\text{per coordinate})$
> Captures "any neighbour fires"; weaker for averaging tasks.
>
> **Learnable (universal) :** $\quad \mathrm{Aggregate}\bigl\{ h_m^{(l)} \bigr\} = \mathrm{MLP}_\theta\!\left( \sum_{m \in N(n)} \mathrm{MLP}_\varphi(h_m^{(l)}) \right) \tag{13.15}$
> Universal approximator for permutation-invariant set functions (Zaheer et al., 2017 — **Deep Sets, 深集合**).

> **Pattern to Notice.** Sum is permutation-invariant because addition is commutative. Mean and max inherit the property pointwise. The MLP version pushes each $h_m$ through a *shared* MLP $\varphi$ — sharing keeps the sum permutation-invariant.

> **Receptive field (感受野).** Each layer reaches one hop further. After $L$ layers, node $n$ depends on all nodes within $L$ hops. Large sparse graphs may need many layers ⇒ **over-smoothing** risk (§13.3.4). A common remedy: add a **super-node** connected to all others, so $L = 2$ already reaches the whole graph.

> **Common Mistake.** Choosing mean aggregation on a problem where degree matters (e.g. citation count). Mean discards exactly the signal you wanted.

---

#### 13.2.4 · The update operator

**Focus.** Make `Update` a small learnable network applied per node.

> **Important Formula — per-node update.**
> $$h_n^{(l+1)} = f\!\left( W_{\text{self}}^{(l)}\, h_n^{(l)} \;+\; W_{\text{neigh}}^{(l)}\, z_n^{(l)} \;+\; b^{(l)} \right). \tag{13.16}$$

**Whole-graph matrix form.** Stack node embeddings into $H^{(l)} \in \mathbb{R}^{N \times D}$ and rewrite:
$$Z^{(l)} = A\, H^{(l)} \quad \text{(sum aggregation)} \tag{13.17}$$
$$H^{(l+1)} = f\!\left( H^{(l)} W_{\text{self}}^{(l)\top} + A H^{(l)} W_{\text{neigh}}^{(l)\top} + \mathbf{1} b^{(l)\top} \right) \tag{13.19}$$

> **Pattern to Notice.** Equation 13.19 looks exactly like a fully-connected layer with $A$ acting as a *learned-graph-aware mixing matrix*. Sparse matrix multiplication makes this cheap when $A$ is sparse.

> **Visual Hint.** Read 13.19 as "for every node, take your own feature through $W_{\text{self}}$, add the (aggregated) neighbour feature through $W_{\text{neigh}}$, push through nonlinearity".

---

#### 13.2.5 · Readout — node classification

**Focus.** Turn final $h_n^{(L)}$ into a class probability $\hat y_n$ for each node.

> **Important Formula.**
> $$\hat y_n = \mathrm{softmax}\!\bigl( W_{\text{out}}\, h_n^{(L)} + b_{\text{out}} \bigr) \tag{13.20}$$
> Cross-entropy loss over the **training nodes** $V_{\text{train}} \subset V$:
> $$\mathcal{L} = -\sum_{n \in V_{\text{train}}} \sum_k y_{n,k}\, \log \hat y_{n,k}. \tag{13.21}$$

**Two settings.**
- **Transductive (直推式) :** the *whole* graph is known at training time; only some node labels are visible. Train on $V_{\text{train}}$, evaluate on $V_{\text{test}}$ in the *same* graph.
- **Inductive (歸納式) :** train on one set of graphs, test on completely new graphs.

> **Common Mistake.** In the transductive setting, the test nodes' *features and edges* are visible — only their *labels* are hidden. You may use them in message passing.

---

#### 13.2.6 · Readout — edge classification

**Focus.** Score every candidate (n, m) pair.

> **Important Formula.**
> $$\hat y_{nm} = \sigma\!\bigl( \mathrm{MLP}\bigl( h_n^{(L)},\, h_m^{(L)} \bigr) \bigr) \tag{13.22}$$
> Train with binary cross-entropy on observed edges as positives and (sampled) non-edges as negatives.

> **Pause and Ask.** Why is feeding $[h_n, h_m]$ to an MLP not symmetric in $(n, m)$ for an undirected graph? How would you fix it?
> (*Hint: symmetrise — use $[h_n + h_m,\ h_n \odot h_m]$, or average the two orderings.*)

---

#### 13.2.7 · Readout — graph classification

**Focus.** Pool all node embeddings into one graph embedding $g$, then classify.

> **Important Formula.**
> $$g = \mathrm{Pool}\bigl(\{ h_n^{(L)} : n \in V \}\bigr), \qquad \hat y = \mathrm{softmax}\!\bigl( W_g\, g + b_g \bigr) \tag{13.23}$$
> The pool may be sum, mean, max, or attention-weighted.

> **Pattern to Notice.** A permutation-**invariant** pool is mandatory here — the graph has no canonical ordering of its nodes, so the predicted label must not change under relabelling.

---

### 13.3 · General graph networks

---

#### 13.3.1 · Graph attention networks (GAT)

**Focus.** Replace uniform neighbour weights by **learned, data-dependent** attention coefficients.

> **Important Formula — GAT layer.**
> $$z_n^{(l)} = \sum_{m \in N(n)} A_{nm}\, h_m^{(l)} \tag{13.24}$$
> subject to
> $$A_{nm} > 0, \qquad \sum_{m \in N(n)} A_{nm} = 1, \tag{13.25, 13.26}$$
> for example
> $$A_{nm} = \frac{\exp\bigl( h_n^{\top} W\, h_m \bigr)}{\sum_{m'} \exp\bigl( h_n^{\top} W\, h_{m'} \bigr)} \tag{13.27}$$
> (**bilinear attention**, $W: D \times D$ learnable) or
> $$A_{nm} = \frac{\exp\bigl\{ \mathrm{MLP}(h_n, h_m) \bigr\}}{\sum_{m'} \exp\bigl\{ \mathrm{MLP}(h_n, h_{m'}) \bigr\}} \tag{13.28}$$
> (**MLP attention**, MLP shared across all node pairs).

**Multi-head GAT.** Run $H$ heads with independent $A_{nm}^{(h)}$; concatenate and project.

> **Key Idea.** Attention is just *learned* aggregation weights — some neighbours matter more than others, and the answer depends on the data, not on graph structure alone.

> **Why This Matters.** A multi-head GAT on the fully-connected graph (every node connected to every node) is exactly the **Transformer (轉換器) encoder**. GNN, attention, and Transformer are one architecture viewed through different graph priors. (Exercise 13.9.)

---

#### 13.3.2 · Edge embeddings

**Focus.** Edges have features too — give them their own embeddings $e_{nm}^{(l)}$.

> **Important Formulas.**
> Update an edge from the two endpoint embeddings and the previous edge embedding:
> $$e_{nm}^{(l+1)} = \mathrm{Update_{edge}}\bigl( e_{nm}^{(l)},\, h_n^{(l)},\, h_m^{(l)} \bigr) \tag{13.29}$$
> Aggregate edges into nodes:
> $$z_n^{(l+1)} = \mathrm{Aggregate_{node}}\bigl\{ e_{nm}^{(l+1)} : m \in N(n) \bigr\} \tag{13.30}$$
> Update nodes from old node + aggregated edges:
> $$h_n^{(l+1)} = \mathrm{Update_{node}}\bigl( h_n^{(l)},\, z_n^{(l+1)} \bigr) \tag{13.31}$$

> **Pattern to Notice.** With edge embeddings, the model can represent **bond type** (in a molecule) or **interaction strength** (in a social graph), not just connectivity.

---

#### 13.3.3 · Graph embedding + full Algorithm 13.2

**Focus.** Add a global state $g^{(l)}$ that summarises the whole graph; let edges, nodes and graph state all influence one another.

![Graph_MessagePassing](https://g0v.hackmd.io/_uploads/S1Zibqegfg.png =300%x)


> **Important Formulas — full message-passing layer.**
> $$e_{nm}^{(l+1)} = \mathrm{Update_{edge}}\bigl( e_{nm}^{(l)},\, h_n^{(l)},\, h_m^{(l)},\, g^{(l)} \bigr) \tag{13.32}$$
> $$z_n^{(l+1)} = \mathrm{Aggregate_{node}}\bigl\{ e_{nm}^{(l+1)} : m \in N(n) \bigr\} \tag{13.33}$$
> $$h_n^{(l+1)} = \mathrm{Update_{node}}\bigl( h_n^{(l)},\, z_n^{(l+1)},\, g^{(l)} \bigr) \tag{13.34}$$
> $$g^{(l+1)} = \mathrm{Update_{graph}}\bigl( g^{(l)},\, \{ h_n^{(l+1)} \},\, \{ e_{nm}^{(l+1)} \} \bigr) \tag{13.35}$$


Algorithm 13.2 — Full graph network

![Algorithm2](https://g0v.hackmd.io/_uploads/r1H-Gcxxzg.png =300%x)

> **Pause and Ask.** Why update edges *first*, then nodes, then the graph state?
> (*Hint: it gives each level the most recent information from the level below.*)

---

#### 13.3.4 · Over-smoothing

**Focus.** Too many layers ⇒ all node embeddings drift towards each other ⇒ the network loses discriminative power.

> **Key Idea — over-smoothing (過度平滑).** Every Aggregate step is a *smoothing* of neighbours into self. Iterate enough and every node looks like the average of the connected component.

**Remedy 1 — Residual connections.**
$$h_n^{(l+1)} = h_n^{(l)} + f\!\left( W_{\text{self}}^{(l)} h_n^{(l)} + W_{\text{neigh}}^{(l)} z_n^{(l)} + b^{(l)} \right) \tag{13.36}$$
The "+ $h_n^{(l)}$" preserves the original signal across layers (cf. ResNets, Ch 9).

**Remedy 2 — Multi-layer readout (jumping knowledge).** Read out from *all* layers, not just the last:
$$\hat y_n = \mathrm{MLP}\!\left( \bigl[\, h_n^{(0)},\, h_n^{(1)},\, \dots,\, h_n^{(L)} \,\bigr] \right) \tag{13.37}$$
Lets the model choose the most informative depth per node.

> **Common Mistake.** "If 3 layers is good, 30 must be better." Without residuals or multi-layer readout, performance typically *peaks at 2–4 layers* and then decays.

---

#### 13.3.5 · Regularisation

**Focus.** Same toolbox as for other deep nets, with graph-aware variants.

- **Dropout (隨機丟棄).** Drop coordinates of $h_n$ during training (standard).
- **DropEdge (隨機丟邊).** Drop a random fraction of edges every step; reduces over-smoothing and over-fitting at once.
- **Node feature noise.** Add Gaussian noise to $h_n^{(0)}$ to discourage memorising features.
- **Weight sharing across layers.** Use the same $W^{(l)}$ for every layer — small data, deep architectures.

> **Pattern to Notice.** Dropping *structure* (DropEdge) is what is new compared with vanilla MLP regularisation. It is the analogue of data augmentation on the graph.

---

### 13.4 · Geometric deep learning (a glimpse)

**Focus.** GNNs are one instance of a wider principle: *build the symmetry into the architecture*.

> **Important Formulas — equivariance with respect to a group $\mathcal{G}$.**
> For each element $g \in \mathcal{G}$ with representation $T_g$ on inputs and $T_g'$ on outputs:
> $$F(T_g\, x) = T_g'\, F(x). \tag{13.38}$$
> Special cases include:
> - $\mathcal{G} = S_N$ (permutations) ⇒ GNNs. $\tag{13.39}$
> - $\mathcal{G} = $ translations on $\mathbb{Z}^2$ ⇒ CNNs. $\tag{13.40}$
> - $\mathcal{G} = \mathrm{SO}(3)$ (3-D rotations) ⇒ equivariant networks for molecules and point clouds. $\tag{13.41}$

> **Why This Matters.** Choosing the right symmetry group is the central design question. CNNs and GNNs are the two most successful answers to date.

---

## Section 5 — Summary

### Today's Core Ideas

1. **Graph data has no canonical ordering.** Models must be permutation-invariant (whole-graph outputs) or permutation-equivariant (node-level outputs).
2. **Aggregate + Update** is the universal template. Aggregate is permutation-invariant by construction; Update is a learnable per-node network.
3. **CNN ⇒ GNN** by removing per-position weights — graph convolution is what is left after enforcing permutation invariance (Eqs 13.8 → 13.9).
4. **Depth = receptive field.** $L$ layers ⇔ $L$-hop neighbourhood. Too many ⇒ over-smoothing; fix with residuals or multi-layer readouts.
5. **GNN ⊃ Deep Sets**; **multi-head GAT on a complete graph = Transformer**. One template, three architectures.

### Formulas to Remember

| Eq    | Name                          | Formula |
| ---   | ---                           | --- |
| 13.3  | Adjacency under relabelling   | $\tilde A = P A P^\top$ |
| 13.9  | Graph convolution from CNN    | $z_i^{(l+1)} = f(w_{\text{neigh}} \sum_{j\in N(i)} z_j^{(l)} + w_{\text{self}} z_i^{(l)} + b)$ |
| 13.10 | Aggregate                     | $z_n^{(l)} = \mathrm{Aggregate}\{ h_m^{(l)} : m \in N(n) \}$ |
| 13.11 | Update                        | $h_n^{(l+1)} = \mathrm{Update}(h_n^{(l)}, z_n^{(l)})$ |
| 13.14 | GCN (Kipf) aggregation        | $z_n = \sum_m h_m / \sqrt{|N(n)|\,|N(m)|}$ |
| 13.15 | Deep-Sets aggregation         | $\mathrm{MLP}_\theta\!\left(\sum_m \mathrm{MLP}_\varphi(h_m)\right)$ |
| 13.19 | Whole-graph layer (matrix)    | $H^{(l+1)} = f\!\left(H^{(l)} W_{\text{self}}^\top + A H^{(l)} W_{\text{neigh}}^\top + \mathbf{1} b^\top\right)$ |
| 13.27 | GAT bilinear attention        | $A_{nm} = \mathrm{softmax}_m(h_n^\top W h_m)$ |
| 13.36 | Residual update               | $h_n^{(l+1)} = h_n^{(l)} + f(W_{\text{self}} h_n^{(l)} + W_{\text{neigh}} z_n^{(l)} + b)$ |

### Problem-Solving Patterns

| If the problem is… | Use… | Why |
| --- | --- | --- |
| Node classification on one big graph (citations) | Transductive GCN, 2–3 layers, Eq 13.14 | Standard, calibrated for degree-skew. |
| Node classification on *new* graphs | Inductive GNN with mean / max aggregation | Don't memorise IDs — must generalise. |
| Edge / link prediction | Eq 13.22 with **symmetrised** MLP | Score pairs; respect symmetry of undirected edges. |
| Graph classification (molecules) | Pool + MLP, Eq 13.23 | Need permutation-**invariant** output. |
| Some neighbours matter more than others | GAT, Eqs 13.27 / 13.28 | Learn the weights from the data. |
| Edge features (bond order, weight) matter | Algorithm 13.2 with edge embeddings | Carry edge info, not only connectivity. |
| Very sparse, large-diameter graph | Add a super-node, or use multi-layer readout (13.37) | Reach the whole graph in few layers without over-smoothing. |
| Deep network keeps getting worse | Residuals (13.36) or DropEdge | Counter over-smoothing and over-fitting. |
| Rotation symmetry (3-D point cloud) | Equivariant network (SO(3)) — Eq 13.41 | Symmetry of the data ≠ permutation. |

### Quick Check

> **Q1.** Two researchers compute features for the same 1000-atom protein but number the atoms differently. Their adjacency matrices look completely different. Are these two valid representations of the same graph? Justify in one line.
> (*Hint: relate to Eq 13.3.*)

> **Q2.** A 12-layer GCN on a small social network performs worse than a 3-layer one. Give two distinct architectural fixes and say what each one prevents.
> (*Hint: §13.3.4.*)

---

## Section 6 — Exercises (Hints Only)

> **13.1.** Show that the sum of two permutation-equivariant maps is permutation-equivariant.
> *Hint.* Write the definition; use linearity of $P$.

> **13.2.** Verify Equation 13.3 by direct computation on the 5-node example with the permutation $(A,B,C,D,E) \to (C,E,A,D,B)$.
> *Hint.* Write $P$, compute $P A P^\top$, compare with the textbook's $A'$.

> **13.3.** Prove that the *mean* aggregation $z_n = \tfrac{1}{|N(n)|}\sum_{m\in N(n)} h_m$ is permutation-invariant in its set argument.
> *Hint.* Both the count $|N(n)|$ and the sum are unchanged under relabelling of $N(n)$.

> **13.4.** Show that Equation 13.9 is a special case of Equation 13.16. Identify $W_{\text{self}}$, $W_{\text{neigh}}$, and the aggregation operator.
> *Hint.* $W_{\text{self}} = w_{\text{self}} I$, $W_{\text{neigh}} = w_{\text{neigh}} I$, sum aggregation.

> **13.5.** A graph has $N$ nodes and average degree $\bar d$. What is the cost of one layer of Equation 13.19 in big-O, treating $A$ as sparse? Compare with a dense MLP on $N D$-dim inputs.
> *Hint.* Sparse mat-vec is $O(N \bar d D)$; dense MLP is $O(N^2 D)$.

> **13.6.** Modify Equation 13.22 so that it is symmetric in $(n, m)$ for undirected graphs.
> *Hint.* Use $[h_n + h_m,\ h_n \odot h_m]$, or symmetrise $\tfrac12\bigl(\mathrm{MLP}(h_n, h_m) + \mathrm{MLP}(h_m, h_n)\bigr)$.

> **13.7.** Show that the symmetric normalisation in Equation 13.14 is invariant under swapping $n$ and $m$ in the denominator. Why is this a desirable property for an undirected graph?
> *Hint.* $\sqrt{|N(n)|\,|N(m)|}$ is symmetric in $n, m$.

> **13.8.** A graph network is run on the complete graph $K_N$ (every node connected to every other node). What does the GCN aggregation (Eq 13.14) reduce to? What does a GAT (Eq 13.27) reduce to?
> *Hint.* GCN ⇒ scaled mean of all features; GAT ⇒ Transformer self-attention over all tokens.

> **13.9. (Transformer = GAT on $K_N$.)** State precisely the architectural correspondence: multi-head GAT layers on the complete graph $\equiv$ Transformer encoder layers. What plays the role of token embeddings? Of positional encoding?
> *Hint.* Token embeddings = node embeddings. There is no graph-structural position; positional encoding is added explicitly to node features.

> **13.10.** Sketch why a GNN with sum aggregation is *strictly more expressive* than one with mean aggregation. Give a small example of two non-isomorphic graphs that mean cannot distinguish but sum can.
> *Hint.* Two regular graphs with different sizes — mean of identical features is identical; sum scales with size.

---

*End of Chapter 13 — Graph Neural Networks · 圖神經網路*
*Reference: Bishop & Bishop, Deep Learning: Foundations and Concepts, Springer 2024, Chapter 13.*
