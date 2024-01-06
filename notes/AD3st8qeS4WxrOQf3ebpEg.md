---
title: "Homotopy Type Theory 讀書會"
tags: math
---

# Homotopy Type Theory 讀書會

> [點此觀看原始內容](https://g0v.hackpad.tw/RBKI9aSJ8Wq)


### 前情提要


pm5 在數學小聚裡提到想找人一起讀 HoTT.

書籍: Homotopy Type Theory: Univalent Foundations of Mathematics
電子版 [http://homotopytypetheory.org/](http://homotopytypetheory.org/)

### Homotopy Type Theory


Homotopy Type Theory is an interpretation of Martin-Löf’s intensional type theory into abstract homotopy theory. Propositional equality is interpreted as homotopy and type isomorphism as homotopy equivalence. Logical constructions in type theory then correspond to homotopy-invariant constructions on spaces, while theorems and even proofs in the logical system inherit a homotopical meaning. As the natural logic of homotopy, type theory is also related to higher category theory as it is used e.g. in the notion of a higher topos.

## 前置知識


### Type Theory

####

- [Intuitionistic Type Theory](https://plato.stanford.edu/entries/type-theory-intuitionistic/), Martin-Löf
- [Proof and Types](http://www.paultaylor.eu/stable/Proofs+Types.html), Jean-Yves Girard
- FLOLAC 14 型別與邏輯 ([video](https://www.youtube.com/watch?v=-CkRUh74Jlo&list=PLIf10Z8n6FbLO6J2a_hL_bZYDRAt9ZMeO)), 柯向上

- 應用: Types and Programming Language, [Benjamin](http://www.cis.upenn.edu/~bcpierce)

相關閒書:
- [數學: 確定性的失落](http://www.books.com.tw/products/0010269515)
- [數學邏輯奇幻之旅(漫畫)](http://www.books.com.tw/products/0010475434)

### Homotopy Theory

- Algebraic Topology 第四章, Allen Hatcher [http://www.math.cornell.edu/~hatcher/AT/ATpage.html](http://www.math.cornell.edu/~hatcher/AT/ATpage.html)

## 章節

Foundations

1 Type theory
1.1 Type theory versus set theory
1.2 Function types
1.3 Universes and families
1.4 Dependent function types (Π-types)
1.5 Product types
1.6 Dependent pair types (Σ-types)
1.7 Coproduct types
1.8 The type of booleans
1.9 The natural numbers
1.10 Pattern matching and recursion
1.11 Propositions as types
1.12 Identity types

2 Homotopy type theory
2.1 Types are higher groupoids
2.2 Functions are functors
2.3 Type families are fibrations
2.4 Homotopies and equivalences
2.5 The higher groupoid structure of type formers
2.6 Cartesian product types
2.7 Σ-types
2.8 The unit type
2.9 Π-types and the function extensionality axiom
2.10 Universes and the univalence axiom
2.11 Identity type
vi Contents
2.12 Coproducts
2.13 Natural numbers
2.14 Example: equality of structures
2.15 Universal properties

3 Sets and logic
3.1 Sets and n-types
3.2 Propositions as types?
3.3 Mere propositions
3.4 Classical vs. intuitionistic logic
3.5 Subsets and propositional resizing
3.6 The logic of mere propositions
3.7 Propositional truncation
3.8 The axiom of choice
3.9 The principle of unique choice
3.10 When are propositions truncated?
3.11 Contractibility

4 Equivalences
4.1 Quasi-inverses
4.2 Half adjoint equivalences
4.3 Bi-invertible maps
4.4 Contractible fibers
4.5 On the definition of equivalences
4.6 Surjections and embeddings
4.7 Closure properties of equivalences
4.8 The object classifier
4.9 Univalence implies function extensionality

5 Induction
5.1 Introduction to inductive types
5.2 Uniqueness of inductive types
5.3 W-types
5.4 Inductive types are initial algebras
5.5 Homotopy-inductive types
5.6 The general syntax of inductive definitions
5.7 Generalizations of inductive types
5.8 Identity types and identity systems

6 Higher inductive types
6.1 Introduction
6.2 Induction principles and dependent paths
6.3 The interval
6.4 Circles and spheres
6.5 Suspensions
6.6 Cell complexes
6.7 Hubs and spokes
6.8 Pushouts
6.9 Truncations
6.10 Quotients
6.11 Algebra
6.12 The flattening lemma
6.13 The general syntax of higher inductive definitions

7 Homotopy n-types
7.1 Definition of n-types
7.2 Uniqueness of identity proofs and Hedberg’s theorem
7.3 Truncations
7.4 Colimits of n-types
7.5 Connectedness
7.6 Orthogonal factorization
7.7 Modalities

II Mathematics

8 Homotopy theory
8.1 π1(S1)
8.2 Connectedness of suspensions
8.3 πk≤n of an n-connected space and πk<n(Sn)
8.4 Fiber sequences and the long exact sequence
8.5 The Hopf fibration
8.6 The Freudenthal suspension theorem
8.7 The van Kampen theorem
8.8 Whitehead’s theorem and Whitehead’s principle
8.9 A general statement of the encode-decode method
viii Contents
8.10 Additional Results
9 Category theory 303
9.1 Categories and precategories
9.2 Functors and transformations
9.3 Adjunctions
9.4 Equivalences
9.5 The Yoneda lemma
9.6 Strict categories
9.7 †-categories
9.8 The structure identity principle
9.9 The Rezk completion
10 Set theory 337
10.1 The category of sets
10.2 Cardinal numbers
10.3 Ordinal numbers
10.4 Classical well-orderings
10.5 The cumulative hierarchy
11 Real numbers 367
11.1 The field of rational numbers
11.2 Dedekind reals
11.3 Cauchy reals
11.4 Comparison of Cauchy and Dedekind reals
11.5 Compactness of the interval
11.6 The surreal numbers

