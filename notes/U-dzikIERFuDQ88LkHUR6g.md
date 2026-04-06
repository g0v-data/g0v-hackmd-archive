# 凸優化 Ch2：Convex Sets 完整教學筆記

> **課程**：ECM5901 Optimization Theory and Application — 賴老師 (NYCU)
> **期中考**：2026/4/14（二）9:00–12:00
> **本筆記對應**：Chapter 2 — Convex Sets

---

## 🗺️ 本章知識地圖

```
2.7  Separating & Supporting Hyperplane Theorems
      ↑
2.6  Dual Cone
      ↑
2.5  Proper Cone & Generalized Inequality
      ↑
2.4  Operations that Preserve Convexity（交集、仿射映射、透視函數...）
      ↑
2.3  重要的凸集實例（Hyperplane, Half-space, Polyhedra, Ball, Ellipsoid, PSD cone）
      ↑
2.2  Cone, Convex Cone, Conic Combination
      ↑
2.1  Convex Set 定義、Convex Combination、Convex Hull  ← 從這裡開始
```

---

# Part 1：Convex Set 的定義與基本概念

## 1.1 直線與線段（Line & Line Segment）

### Line（直線）

給定兩個不同的點 x₁, x₂ ∈ ℝⁿ，通過它們的直線可以寫成：

```
L(θ) = θ(x₁ - x₂) + x₂ = θx₁ + (1-θ)x₂,   θ ∈ ℝ（任意實數）
```

**直覺**：θ 可以跑遍所有實數，所以 L 是一條無限延伸的直線。

- θ = 0 時，L = x₂
- θ = 1 時，L = x₁
- θ = 0.5 時，L = 中點
- θ = 2 時，L 跑到 x₁ 的「另一邊」更遠處

### Line Segment（線段）

把 θ 限制在 [0, 1]：

```
L(θ) = θx₁ + (1-θ)x₂,   0 ≤ θ ≤ 1
```

這就是連接 x₁ 和 x₂ 的線段。

## 1.2 Convex Set（凸集）的定義 ⭐⭐⭐

**定義**：集合 C ⊆ ℝⁿ 是凸集，如果對 C 中**任意**兩點 x₁, x₂ 和**任意** θ ∈ [0, 1]：

```
θx₁ + (1-θ)x₂ ∈ C
```

### 白話翻譯

在 C 中隨便挑兩點，把它們連成線段，線段上**每一個點**都還在 C 裡面。

### 圖形化判斷

- ✅ 凸：實心圓、三角形、正方形、整個 ℝⁿ、空集合、單一個點
- ❌ 非凸：L 形、甜甜圈、星形、月牙形（只要你能在集合裡找到兩點，連線的某一段跑出集合外，就不是凸的）

### 證明一個集合是凸的標準步驟

1. 取**任意** x₁, x₂ ∈ C，**任意** θ ∈ [0, 1]
2. 計算 θx₁ + (1-θ)x₂
3. 證明它滿足 C 的定義條件（即屬於 C）

## 1.3 Convex Combination（凸組合）

給定 k 個點 x₁, ..., xₖ ∈ ℝⁿ，它們的**凸組合**是：

```
θ₁x₁ + θ₂x₂ + ... + θₖxₖ
```

其中 θᵢ ≥ 0 且 Σθᵢ = 1。

**直覺**：凸組合就是「加權平均」。權重都非負，加起來等於 1。

**與一般線性組合的差異**：

| 種類 | 條件 |
|------|------|
| 線性組合（Linear Combination）| θᵢ ∈ ℝ，沒有限制 |
| 仿射組合（Affine Combination）| Σθᵢ = 1 |
| **凸組合（Convex Combination）**| **θᵢ ≥ 0 且 Σθᵢ = 1** |
| 錐組合（Conic Combination）| θᵢ ≥ 0 |

## 1.4 Convex Hull（凸包）⭐

集合 S 的凸包定義為 S 中所有點的所有凸組合：

```
conv(S) = {θ₁x₁ + ... + θₖxₖ : xᵢ ∈ S, θᵢ ≥ 0, Σθᵢ = 1}
```

### 兩個重要性質

1. **conv(S) 是凸的**
2. **conv(S) 是包含 S 的最小凸集**

### 直覺

把橡皮筋套在 S 的所有點外面，橡皮筋圍出來的區域就是 conv(S)。

### 特例

如果 S 本身已經是凸的，那 conv(S) = S。

---

# Part 2：Cone（錐）

## 2.1 Cone 的定義

集合 C ⊆ ℝⁿ 是 **cone**，如果對所有 x ∈ C 和 θ ≥ 0：

```
θx ∈ C
```

**直覺**：從原點出發，沿著 C 裡的任何方向，無限延伸，都還在 C 裡面。

**注意**：cone 不一定是凸的！（想像兩條從原點出發的射線，但中間不包含）

## 2.2 Convex Cone（凸錐）⭐

C 是 **convex cone**，如果對所有 x₁, x₂ ∈ C 和 θ₁, θ₂ ≥ 0：

```
θ₁x₁ + θ₂x₂ ∈ C
```

**直覺**：convex cone = cone + convex。不但可以沿任何方向伸縮，還可以把兩個方向「混合」。

## 2.3 Conic Combination & Conic Hull

**Conic Combination（錐組合）**：

```
θ₁x₁ + ... + θₖxₖ,   θᵢ ≥ 0
```

跟凸組合的差別：不需要 Σθᵢ = 1。

**Conic Hull（錐包）**= S 中所有點的錐組合集合 = 包含 S 的最小錐。

---

# Part 3：重要的凸集實例 ⭐⭐⭐

## 3.1 Hyperplane（超平面）

```
H = {x ∈ ℝⁿ : aᵀx = b}
```

其中 a ∈ ℝⁿ（a ≠ 0）是法向量，b ∈ ℝ。

### 直覺

- 在 ℝ² 中，超平面就是一條**直線**
- 在 ℝ³ 中，超平面就是一個**平面**
- 在 ℝⁿ 中，超平面是 n-1 維的「切片」

### 凸性證明（講義 p.6，考試常考的證明格式）

取 x₁, x₂ ∈ H（即 aᵀx₁ = b, aᵀx₂ = b），θ ∈ [0, 1]。

```
aᵀ(θx₁ + (1-θ)x₂) = θ·aᵀx₁ + (1-θ)·aᵀx₂    （aᵀ的線性性）
                     = θ·b + (1-θ)·b
                     = b
```

所以 θx₁ + (1-θ)x₂ ∈ H。■

## 3.2 Half-space（半空間）

```
F = {x ∈ ℝⁿ : aᵀx ≤ b}
```

### 直覺

超平面把 ℝⁿ 切成兩半，取其中一半（包含邊界）。

### 凸性

同樣用線性性質：θ(aᵀx₁) + (1-θ)(aᵀx₂) ≤ θb + (1-θ)b = b。■

## 3.3 Polyhedra（多面體）⭐

```
P = {x ∈ ℝⁿ : aⱼᵀx ≤ bⱼ, j = 1,...,m ;  cₖᵀx = dₖ, k = 1,...,r}
```

### 直覺

多面體 = 有限個半空間和超平面的**交集**。

用矩陣表示：

```
P = {x : Ax ≤ b, Cx = d}
```

其中 A 的每一列是 aⱼᵀ。

### 凸性

每個半空間和超平面都是凸的，凸集的交集還是凸的（後面會證明），所以 Polyhedra 是凸的。

### 💡 LP 的可行域就是 Polyhedra！

## 3.4 Euclidean Ball（歐氏球）⭐

```
B₂(xc, r) = {x ∈ ℝⁿ : ‖x - xc‖₂ ≤ r}
```

- xc：球心
- r > 0：半徑

### 凸性證明（講義 p.8，考試重點！）

取 x₁, x₂ ∈ B₂(xc, r)，即 ‖x₁ - xc‖₂ ≤ r, ‖x₂ - xc‖₂ ≤ r。取 θ ∈ [0, 1]。

```
‖θx₁ + (1-θ)x₂ - xc‖₂

= ‖θ(x₁ - xc) + (1-θ)(x₂ - xc)‖₂       （把 xc 拆開）

≤ θ‖x₁ - xc‖₂ + (1-θ)‖x₂ - xc‖₂         （三角不等式 + 齊次性）

≤ θr + (1-θ)r                                （因為兩者都 ≤ r）

= r
```

所以 θx₁ + (1-θ)x₂ ∈ B₂(xc, r)。■

**這個證明模板非常重要！** 用到了 Norm 的三角不等式和齊次性。

## 3.5 Ellipsoid（橢球）⭐⭐

```
ε(xc, P) = {x ∈ ℝⁿ : (x - xc)ᵀ P⁻¹ (x - xc) ≤ 1}
```

其中 P ≻ 0（正定矩陣）。

### 三種等價表述（講義 p.9）

**(1)** 原始定義（如上）

**(2)** 用 Norm 表示：

```
ε(xc, P) = {x : ‖P⁻¹/²(x - xc)‖₂ ≤ 1}
```

**(3)** 用參數化表示：

```
ε(xc, P) = {P¹/²u + xc : ‖u‖₂ ≤ 1}
```

### 直覺

- P = r²I 時，橢球退化為半徑 r 的 Euclidean ball
- P 的特徵值決定橢球各軸的長度
- P 的特徵向量決定橢球的方向

### 凸性證明（兩種方法，講義 p.16）

**方法 1（Image of affine function）**：

令 f(u) = P¹/²u + xc（仿射函數），B₂(0,1) 是凸的。

```
ε(xc, P) = f(B₂(0, 1)) = 仿射函數的 image
```

仿射函數保持凸性 → ε(xc, P) 是凸的。■

**方法 2（Inverse image of affine function）**：

令 g(x) = P⁻¹/²(x - xc)（仿射函數），B₂(0,1) 是凸的。

```
ε(xc, P) = g⁻¹(B₂(0, 1)) = 仿射函數的 inverse image
```

仿射函數的 inverse image 保持凸性 → ε(xc, P) 是凸的。■

## 3.6 Positive Semidefinite Cone Sⁿ₊ ⭐⭐

```
Sⁿ₊ = {A ∈ Sⁿ : A ⪰ 0} = {A ∈ ℝⁿˣⁿ : A = Aᵀ, xᵀAx ≥ 0 ∀x}
```

### Sⁿ₊ 是 convex cone

**Proof**：

**(i) 是 cone**：若 A ⪰ 0，θ ≥ 0，則對任意 x：

```
xᵀ(θA)x = θ(xᵀAx) ≥ 0   （因為 θ ≥ 0 且 xᵀAx ≥ 0）
```

所以 θA ⪰ 0。■

**(ii) 是 convex**：若 A, B ⪰ 0，θ₁, θ₂ ≥ 0，則對任意 x：

```
xᵀ(θ₁A + θ₂B)x = θ₁(xᵀAx) + θ₂(xᵀBx) ≥ 0
```

所以 θ₁A + θ₂B ⪰ 0。■

### Sⁿ₊ 可以表示為半空間的交集（講義 p.13）⭐

```
Sⁿ₊ = ∩_{x∈ℝⁿ} {A ∈ Sⁿ : xᵀAx ≥ 0}
```

**關鍵技巧**：xᵀAx = tr(Axxᵀ) = ⟨xxᵀ, A⟩_F

所以每個 {A : xᵀAx ≥ 0} 是 Sⁿ 空間中的一個半空間（因為 ⟨xxᵀ, A⟩_F ≥ 0 是關於 A 的線性不等式）。

Sⁿ₊ 是無限多個半空間的交集 → 凸。（交集保持凸性）

---

# Part 4：保持凸性的運算 ⭐⭐⭐

這是本章最核心的部分。考試經常會給你一個集合，要你證明它是凸的。最常見的策略就是把它拆解成「已知凸集 + 保持凸性的運算」。

## 4.1 Intersection（交集）

**定理**：

- 若 S₁, S₂ 是凸集，則 S₁ ∩ S₂ 是凸集。
- 更一般地，若 Sα 對所有 α ∈ A 都是凸的（A 可以是無限集），則 ∩_{α∈A} Sα 是凸集。

### 證明（標準範本）

取 x, y ∈ S₁ ∩ S₂，θ ∈ [0,1]。

因為 x, y ∈ S₁ 且 S₁ 凸 → θx + (1-θ)y ∈ S₁。
因為 x, y ∈ S₂ 且 S₂ 凸 → θx + (1-θ)y ∈ S₂。

所以 θx + (1-θ)y ∈ S₁ ∩ S₂。■

### ⚠️ 注意

**聯集（Union）不一定保持凸性！** 兩個不相交的圓都是凸的，但它們的聯集不是凸的。

## 4.2 Affine Function（仿射函數）⭐⭐⭐

f(x) = Ax + b，其中 A ∈ ℝᵐˣⁿ，b ∈ ℝᵐ。（b = 0 時就是線性函數）

**定理**：若 S 是凸集，f 是仿射函數，則：

**(a) Image f(S) 是凸的**

**(b) Inverse Image f⁻¹(S) = {x : f(x) ∈ S} 是凸的**

### Image 的證明

取 y₁, y₂ ∈ f(S)，即存在 x₁, x₂ ∈ S 使得 y₁ = Ax₁+b, y₂ = Ax₂+b。

```
θy₁ + (1-θ)y₂ = θ(Ax₁+b) + (1-θ)(Ax₂+b)
               = A(θx₁ + (1-θ)x₂) + b
               = f(θx₁ + (1-θ)x₂)
```

因為 S 凸，θx₁ + (1-θ)x₂ ∈ S，所以 f(θx₁ + (1-θ)x₂) ∈ f(S)。■

### 💡 考試超級常用！

很多證明凸性的題目，關鍵策略就是：

> **找一個仿射函數 f 和一個已知的凸集，把目標集合寫成 f(已知凸集) 或 f⁻¹(已知凸集)**

例如橢球的凸性證明就是用這個策略。

## 4.3 Sum & Direct Product（和與直積）

若 S₁, S₂ ⊆ ℝⁿ 是凸的，則：

**(a) Direct Product（直積）**：

```
S₁ × S₂ = {(x₁, x₂) ∈ ℝ²ⁿ : x₁ ∈ S₁, x₂ ∈ S₂}    是凸的
```

**(b) Sum（Minkowski sum）**：

```
S₁ + S₂ = {x₁ + x₂ : x₁ ∈ S₁, x₂ ∈ S₂}    是凸的
```

### Sum 的證明思路（很巧妙！）

定義 f(x₁, x₂) = x₁ + x₂（線性函數）。

S₁ + S₂ = f(S₁ × S₂)。

S₁ × S₂ 凸（由 (a)），f 是線性的 → f(S₁ × S₂) 凸（仿射函數的 image 保凸）。■

## 4.4 Perspective Function（透視函數）⭐

```
P(z, t) = z/t,    其中 z ∈ ℝⁿ, t > 0
```

domain 是 ℝⁿ × ℝ₊₊（最後一個分量必須為正）。

**定理**：

**(a)** 若 S ⊆ ℝⁿ × ℝ₊₊ 凸，則 P(S) 凸。

**(b)** 若 S ⊆ ℝⁿ 凸，則 P⁻¹(S) 凸。

### 直覺

透視函數就是「從原點看出去」的投影。就像針孔相機的成像原理——遠處的東西看起來小，近處的東西看起來大。

### 證明思路（講義 p.17–18）

取 (z₁, t₁), (z₂, t₂) ∈ S（所以 t₁, t₂ > 0）。

P(z₁, t₁) = z₁/t₁，P(z₂, t₂) = z₂/t₂。

需要證明：θ·P(z₁,t₁) + (1-θ)·P(z₂,t₂) ∈ P(S)。

關鍵 trick：令

```
μ = θt₁ / (θt₁ + (1-θ)t₂)
```

那麼 μ ∈ (0,1)，然後可以驗證：

```
θ·(z₁/t₁) + (1-θ)·(z₂/t₂) = P(μ(z₁,t₁) + (1-μ)(z₂,t₂))
```

因為 S 凸，μ(z₁,t₁) + (1-μ)(z₂,t₂) ∈ S，所以右邊 ∈ P(S)。■

## 4.5 Linear Fractional Function（線性分式函數）

```
f(x) = (Ax + b) / (cᵀx + d),    dom f = {x : cᵀx + d > 0}
```

這是「仿射函數 + 透視函數」的組合：f = P ∘ g，其中 g(x) = [Ax+b; cᵀx+d] 是仿射的。

**定理**：若 S ⊆ dom f 凸，則 f(S) 凸。

**Proof**：S 凸 → g(S) 凸（仿射保凸）→ P(g(S)) 凸（透視保凸）。■

---

# Part 5：Open & Closed Sets（開集與閉集）

## 5.1 Interior Point（內點）

x 是集合 C 的**內點**，如果存在 ε > 0 使得以 x 為圓心、ε 為半徑的球**完全包含在 C 裡面**：

```
B(x, ε) = {z : ‖z - x‖ < ε} ⊆ C
```

C 的所有內點的集合叫做 C 的**interior（內部）**，記作 int C。

### 例子

B(0, 1) = {y : ‖y‖ ≤ 1}（閉球）

- int B(0, 1) = {y : ‖y‖ < 1}（開球，邊界上的點不是內點）

## 5.2 Open Set（開集）

C 是開集 ⟺ int C = C ⟺ C 裡的每一點都是內點。

**例子**：(a, b) = {x ∈ ℝ : a < x < b} 是開集。

## 5.3 Closed Set（閉集）

C 是閉集 ⟺ 補集 ℝⁿ \ C 是開集。

**例子**：[a, b] = {x ∈ ℝ : a ≤ x ≤ b} 是閉集。

### 直覺對照表

| | 開集 | 閉集 | 既非開也非閉 |
|---|------|------|------------|
| ℝ¹ | (a, b) | [a, b] | [a, b) 或 (a, b] |
| ℝⁿ | {y : ‖y‖ < 1} | {y : ‖y‖ ≤ 1} | 很多例子 |

### 特殊情況

ℝⁿ 和 ∅ 同時是開集也是閉集（唯二的例子）。

---

# Part 6：Proper Cone & Generalized Inequality ⭐⭐

## 6.1 Proper Cone（正規錐）

一個 cone K ⊆ ℝⁿ 是 proper cone，如果同時滿足：

1. **Convex**（凸的）
2. **Closed**（閉的）
3. **Solid**（有非空的 interior，即 int K ≠ ∅）
4. **Pointed**（尖的：不包含整條直線。等價於 x ∈ K 且 -x ∈ K → x = 0）

### 例子

| K | 是否 proper cone？ |
|---|-------------------|
| ℝⁿ₊ = {x : xᵢ ≥ 0 ∀i} | ✅ 是 |
| Sⁿ₊ | ✅ 是 |
| {0} | ❌ 不是（不 solid，interior 為空）|
| ℝⁿ | ❌ 不是（不 pointed，包含直線）|
| ℝ²₊ 但去掉邊界 | ❌ 不是（不 closed）|

## 6.2 Generalized Inequality（推廣的不等式）⭐⭐

給定 proper cone K，定義**偏序關係**：

```
x ≤_K y  ⟺  y - x ∈ K        （「小於等於」）
x <_K y  ⟺  y - x ∈ int K    （「嚴格小於」）
```

### 最常見的特例

**K = ℝ₊（非負實數）**：

```
a ≤_{ℝ₊} b  ⟺  b - a ≥ 0  ⟺  a ≤ b    （就是普通的 ≤）
```

**K = ℝⁿ₊（分量都非負的向量）**：

```
a ≤_{ℝⁿ₊} b  ⟺  bᵢ - aᵢ ≥ 0 ∀i  ⟺  aᵢ ≤ bᵢ ∀i    （分量逐一比較）
```

**K = Sⁿ₊（PSD cone）**：

```
A ≤_{Sⁿ₊} B  ⟺  B - A ⪰ 0    （B - A 是 PSD）
```

這就是講義裡常見的 A ⪯ B（Löwner ordering）。

## 6.3 Generalized Inequality 的性質

設 ≤_K 是由 proper cone K 定義的偏序。

| 性質 | 數學表述 |
|------|---------|
| 加法保序 | x ≤_K y, u ≤_K v → x+u ≤_K y+v |
| 傳遞性 | x ≤_K y, y ≤_K z → x ≤_K z |
| 正純量保序 | x ≤_K y, θ ≥ 0 → θx ≤_K θy |
| 自反性 | x ≤_K x |
| 反對稱性 | x ≤_K y, y ≤_K x → x = y |
| 極限保序 | xᵢ ≤_K yᵢ, xᵢ→x, yᵢ→y → x ≤_K y |

嚴格不等式 <_K 的性質：

| 性質 | 數學表述 |
|------|---------|
| 嚴格 + 非嚴格 | x <_K y, u ≤_K v → x+u <_K y+v |
| 正純量保嚴格序 | x <_K y, θ > 0 → θx <_K θy |

---

# Part 7：Dual Cone（對偶錐）⭐⭐

## 7.1 定義

K 是 cone，K 的 **dual cone** 定義為：

```
K* = {y : ⟨x, y⟩ ≥ 0,  ∀x ∈ K}
```

### 直覺

K* 裡的向量 y 跟 K 裡的**每一個**向量的夾角都 ≤ 90°（因為內積 ≥ 0）。

### 重要性質

- K* 永遠是 convex cone（不管 K 是不是凸的）
- 如果 K 是 proper cone，K* 也是 proper cone

## 7.2 Self-dual（自對偶）⭐

K 是 self-dual 如果 K* = K。

### 兩個最重要的例子

**ℝⁿ₊ 是 self-dual**：

```
(ℝⁿ₊)* = {y : xᵀy ≥ 0, ∀x ∈ ℝⁿ₊} = ℝⁿ₊
```

**Sⁿ₊ 是 self-dual**：

```
(Sⁿ₊)* = {Y ∈ Sⁿ : ⟨X, Y⟩_F ≥ 0, ∀X ⪰ 0} = Sⁿ₊
```

### Sⁿ₊ 自對偶的證明思路

**(⊇)** 若 Y ⪰ 0，X ⪰ 0，則 ⟨X, Y⟩_F = tr(YX) ≥ 0。

（因為 YX 的特徵值都 ≥ 0，所以 trace ≥ 0。更精確的說法：tr(YX) = tr(Y^(1/2) X Y^(1/2)) ≥ 0。）

**(⊆)** 若 Y ∉ Sⁿ₊，則存在特徵值 λ < 0 和對應特徵向量 v。取 X = vvᵀ ⪰ 0，則 ⟨X, Y⟩_F = tr(Yvvᵀ) = vᵀYv = λ < 0，矛盾。■

---

# Part 8：Separating & Supporting Hyperplane Theorems ⭐⭐⭐

## 8.1 Separating Hyperplane Theorem（分離超平面定理）

**定理**：若 C 和 D 是非空、不相交的凸集（C ∩ D = ∅），則存在 a ≠ 0 和 b 使得：

```
aᵀx ≤ b,  ∀x ∈ C
aᵀx ≥ b,  ∀x ∈ D
```

**直覺**：兩個不重疊的凸集之間，一定可以插一個超平面把它們分開。

### 為什麼這麼重要？

這是 **duality theory（對偶理論，Ch5）** 的基礎！也是 SVM（支持向量機）的理論根基。

## 8.2 Supporting Hyperplane（支撐超平面）

**定義**：C ⊆ ℝⁿ 是非空集合，x₀ ∈ bd C（邊界上的點）。若存在 a ≠ 0 使得：

```
aᵀx ≤ aᵀx₀,  ∀x ∈ C
```

則超平面 {x : aᵀx = aᵀx₀} 是 C 在 x₀ 處的**支撐超平面**。

### 直覺

支撐超平面就是在集合的邊界點上「切」一刀，整個集合都在這一刀的同一側。

## 8.3 Supporting Hyperplane Theorem

**定理**：對任何非空凸集 C 和邊界點 x₀ ∈ bd C，一定存在 C 在 x₀ 處的支撐超平面。

**直覺**：凸集的邊界足夠「光滑」（即使有角也沒關係），永遠可以找到一個超平面在邊界上「靠」著它。

---

# 📋 Ch2 考試重點 Cheat Sheet

## 必背定義（5 個）

| # | 定義 | 核心公式 |
|---|------|---------|
| 1 | Convex Set | θx₁ + (1-θ)x₂ ∈ C, ∀x₁,x₂ ∈ C, θ ∈ [0,1] |
| 2 | Convex Cone | θ₁x₁ + θ₂x₂ ∈ C, ∀x₁,x₂ ∈ C, θ₁,θ₂ ≥ 0 |
| 3 | Convex Hull | conv(S) = {Σθᵢxᵢ : xᵢ ∈ S, θᵢ ≥ 0, Σθᵢ = 1} |
| 4 | Proper Cone | convex + closed + solid + pointed |
| 5 | Dual Cone | K* = {y : ⟨x,y⟩ ≥ 0 ∀x ∈ K} |

## 必背的重要凸集（6 個）

| 凸集 | 定義 | 備註 |
|------|------|------|
| Hyperplane | {x : aᵀx = b} | 是仿射集 |
| Half-space | {x : aᵀx ≤ b} | 最基本的凸集 |
| Polyhedra | {x : Ax ≤ b, Cx = d} | = 半空間 ∩ 超平面 |
| Euclidean Ball | {x : ‖x-xc‖₂ ≤ r} | 用三角不等式證凸 |
| Ellipsoid | {x : (x-xc)ᵀP⁻¹(x-xc) ≤ 1} | P ≻ 0；用仿射映射證凸 |
| PSD Cone Sⁿ₊ | {A ∈ Sⁿ : A ⪰ 0} | convex cone, self-dual |

## 保持凸性的運算（6 種，必背！）

| 運算 | S₁, S₂ 凸 → 結果凸？ |
|------|-------------------|
| **交集** S₁ ∩ S₂ | ✅ |
| **聯集** S₁ ∪ S₂ | ❌ 不一定！ |
| **Affine Image** f(S) = {Ax+b : x ∈ S} | ✅ |
| **Affine Inverse Image** f⁻¹(S) | ✅ |
| **Perspective Image** P(S) | ✅ |
| **Linear Fractional Image** | ✅ |

## 證明凸性的三大策略

1. **直接用定義**：取 x₁, x₂ ∈ S, θ ∈ [0,1]，證 θx₁+(1-θ)x₂ ∈ S
2. **寫成已知凸集的交集**（交集保凸）
3. **寫成已知凸集經仿射函數的 image 或 inverse image**（仿射保凸）

## 常見考試題型

1. **「證明 S 是凸集」**→ 用上面三大策略之一
2. **「S 是否為凸集？」**→ 是的話證明，不是的話舉反例（找兩點使得線段跑出去）
3. **「Sⁿ₊ 的性質」**→ convex cone, proper cone, self-dual, 是半空間的交集
4. **「Ellipsoid 是凸的」**→ 用仿射映射的 image 或 inverse image
5. **「Separating hyperplane」**→ 兩不相交凸集之間找分離超平面
6. **Generalized inequality 的性質**→ 用 K 的定義推導

## 常見陷阱

- 聯集不保凸！只有交集保凸
- Cone 不一定是 convex——convex cone 才是
- Proper cone 需要同時滿足四個條件，少一個都不行
- Dual cone K* 永遠是 convex cone（即使 K 不是凸的）
- Perspective function 的 domain 要求最後一個分量 > 0
- Ellipsoid 的 P 必須是 positive definite（不是 PSD！）

---

> 💪 Ch2 最核心的考試能力是**判斷和證明凸性**。
> 建議練習：
> 1. 把 Ball 的凸性證明完整寫一遍（模板化的三角不等式論證）
> 2. 練習用「仿射映射保凸」來證明 Ellipsoid 的凸性
> 3. 確保會證明 Sⁿ₊ 是 convex cone
> 4. 搞清楚每一種「保凸運算」的證明邏輯
>
> 有任何不懂的地方，隨時問我！