
# 🧠 关系代数 Relation Algebra 复习笔记

## ✅ 1. 定义

**关系代数**是一个包含集合与关系运算的布尔代数结构：

$A=(A, 0, 1, +, ⋅, −, 1′, ⌣, ∘)$

其中：

- $0,\ 1$：最小元与最大元（空关系与全集）
    
- $+$、$\cdot$、$-$：并、交、补
    
- $1'$：恒等关系 ${(x,x)}$  reflective
    
- ${}^{\smile}$：对合（converse）Symmetric
    
- $\circ$：复合（composition）Transitive
    

---

## ✅ 2. 元素解释

- 元素 $a \in A$ 表示一个**抽象的二元关系**
    
- 运算对应关系上的集合操作
    

---

## ✅ 3. 对合运算

$a⌣={(y,x)∣(x,y)∈a}a^{\smile} = \{(y,x) \mid (x,y) \in a\}$

交换有序对左右。

---

## ✅ 4. 复合运算（关键）

$a∘b={(x,z)∣∃y, (x,y)∈a∧(y,z)∈b}a \circ b = \{(x,z) \mid \exists y,\ (x,y) \in a \land (y,z) \in b\}$

从 $x$ 经 $a$ 到 $y$，再经 $b$ 到 $z$，得出 $(x,z)$

---

## ✅ 5. Representation（表征）

表示是将抽象代数 $\mathcal{A}$ 映射到具体集合 $X$ 上的关系代数 $\mathcal{F}(X)$ 的同态：

$h:A→F(X)h : \mathcal{A} \to \mathcal{F}(X)$

要求保持所有运算：

- $h(a + b) = h(a) \cup h(b)$
    
- $h(a \cdot b) = h(a) \cap h(b)$
    
- $h(-a) = (X \times X) \setminus h(a)$
    
- $h(a^{\smile}) = h(a)^{-1}$
    
- $h(a \circ b) = h(a) \circ h(b)$
    
- $h(1') = {(x,x) \mid x \in X}$
    

---

## ✅ 6. Atom（原子）

- 每个原子是一个极小的非空关系
    
- 对于 $X$，原子数 = $|X \times X| = n^2$
    
- 每个原子形如 ${(x,y)}$，不可再拆
    

---

## ✅ 7. Identity 下的原子

- 若 ${(x,x)} \subseteq 1'$，则该原子“在恒等关系之下”（below identity）
    

---

## ✅ 8. Composition 表格（实用）

枚举原子 $r_i, r_j$：

- 若 $r_i = {(x,y)}$, $r_j = {(y,z)}$
    
- 则 $r_i \circ r_j = {(x,z)}$
    

否则为空集 $\emptyset$

---

## ✅ 9. 典型记忆口诀

> **加交补对合复，恒等单位满集数**  
> 运算守恒映射清，抽象映实是表征。

---
