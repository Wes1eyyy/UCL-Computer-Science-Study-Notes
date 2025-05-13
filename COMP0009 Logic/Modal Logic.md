## 📘 Modal Logic Summary

### 🔹 What is Modal Logic?

**Modal Logic** extends classical logic with operators to express **necessity** and **possibility**:

- $◇\varphi$ means “possibly $\varphi$”
    
- $□\varphi$ means “necessarily $\varphi$”
    

---

### 🔹 Kripke Semantics

A **Kripke Model** is a triple $M = (W, R, V)$:

- $W$: a set of possible worlds
    
- $R \subseteq W \times W$: accessibility relation between worlds
    
- $V$: valuation function assigning truth to atomic propositions in each world
    

**Semantics**:

- $M, w \vDash □\varphi \iff \text{for all } w' \text{ such that } w R w',\ M, w' \vDash \varphi$
    
- $M, w \vDash ◇\varphi \iff \text{there exists } w' \text{ such that } w R w',\ M, w' \vDash \varphi$
    

---

### 🔹 Frame Properties and Modal Systems

|Property|System|Axiom|Description|
|---|---|---|---|
|**Reflexive**|T|$□\varphi \rightarrow \varphi$|Each world can access itself ($\forall w,\ w R w$)|
|**Symmetric**|B|$\varphi \rightarrow □◇\varphi$|If $w R v$ then $v R w$|
|**Transitive**|S4|$□\varphi \rightarrow □□\varphi$|If $w R v$ and $v R u$ then $w R u$|

---

### 🔹 Summary of Logical Systems

- **T System**: reflexive frames, supports $□\varphi \rightarrow \varphi$
    
- **B System**: reflexive + symmetric frames, supports $\varphi \rightarrow □◇\varphi$
    
- **S4 System**: reflexive + transitive frames, supports $□\varphi \rightarrow □□\varphi$
    

---
## ✅ 常用的模态逻辑等价公式（恒等式）

### 1. 否定与模态运算的等价：

- ¬□ϕ ≡ ◇¬ϕ  （“不是必然” ⇔ “可能不”）
    
- ¬◇ϕ ≡ □¬ϕ  （“不可能” ⇔ “必然不”）
    

举例：  
¬□¬p ≡ ◇p  
¬◇p ≡ □¬p

---

### 2. 模态运算之间的关系（框架无关）：

- □ϕ → ϕ（**在 T 系统中成立：前提是反身性**）
    
- □ϕ → □□ϕ（**在 S4 系统中成立：传递性**）
    
- ◇ϕ → □◇ϕ（**在 B 系统中成立：对称性**）
    

---

### 3. 蕴含与模态的分配（仅部分框架有效）：

- □(ϕ → ψ) → (□ϕ → □ψ) （**K系统成立，最弱模态系统**）
    
- ◇(ϕ ∨ ψ) ≡ ◇ϕ ∨ ◇ψ
    
- □(ϕ ∧ ψ) ≡ □ϕ ∧ □ψ
    
- ◇(ϕ ∧ ψ) → ◇ϕ ∧ ◇ψ（**注意：不能逆推出**）
    

---

### 4. 双重模态运算（需特定 frame 性质）：

- □ϕ ≡ □□ϕ（若 frame 为**传递**）
    
- ◇ϕ ≡ ◇◇ϕ（若 frame 为**可达性可逆**）
    

---

### 5. 模态演算中有用的转化技巧：

- p → ◇q ≡ ¬p ∨ ◇q
    
- □(p → q) ≡ (□p → □q) （在某些系统中成立）
    

---

## 📌 推荐记忆核心三条：

1. ¬□ϕ ≡ ◇¬ϕ
    
2. ¬◇ϕ ≡ □¬ϕ
    
3. □(ϕ ∧ ψ) ≡ □ϕ ∧ □ψ
    

---
