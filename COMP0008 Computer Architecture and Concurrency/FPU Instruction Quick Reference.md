## 🧠 MIPS 浮点指令总览（FPU Instruction Summary）

### 🧾 一、数据传输指令（Data Transfer）

```mips
lwc1  $fX, offset($rY)     # Load word (32-bit float) from memory to $fX
swc1  $fX, offset($rY)     # Store word from $fX to memory

ldc1  $fX, offset($rY)     # Load doubleword (64-bit float) to $fX/$fX+1
sdc1  $fX, offset($rY)     # Store doubleword from $fX/$fX+1 to memory

mtc1  $rX, $fY             # Move 32-bit int register $rX → float register $fY
mfc1  $rX, $fY             # Move float register $fY → int register $rX

dmfc1 $rX, $fY             # Move double precision value (for 64-bit MIPS)
dmtc1 $rX, $fY             # Move 64-bit int into float reg (MIPS64)
```

---

### 🧮 二、算术运算指令（Arithmetic Operations）

```mips
add.s $fD, $fS, $fT        # $fD = $fS + $fT (single precision)
sub.s $fD, $fS, $fT        # $fD = $fS - $fT
mul.s $fD, $fS, $fT        # $fD = $fS * $fT
div.s $fD, $fS, $fT        # $fD = $fS / $fT

add.d $fD, $fS, $fT        # Double precision versions（64-bit）
sub.d $fD, $fS, $fT
mul.d $fD, $fS, $fT
div.d $fD, $fS, $fT
```

---

### 🔄 三、类型转换指令（Type Conversion）

```mips
cvt.s.w  $fD, $fS          # Convert 32-bit int → single float
cvt.d.w  $fD, $fS          # Convert 32-bit int → double float

cvt.w.s  $fD, $fS          # Convert single float → 32-bit int
cvt.w.d  $fD, $fS          # Convert double float → 32-bit int

cvt.d.s  $fD, $fS          # Convert single → double
cvt.s.d  $fD, $fS          # Convert double → single
```

---

### ⚖️ 四、比较指令（Comparison Instructions）

```mips
c.eq.s  $fS, $fT           # Set condition flag if $fS == $fT
c.lt.s  $fS, $fT           # Set condition flag if $fS < $fT
c.le.s  $fS, $fT           # Set condition flag if $fS ≤ $fT

c.eq.d, c.lt.d, c.le.d     # Double precision versions
```

配合**条件分支指令**使用：

```mips
bc1t LABEL                 # Branch if condition true
bc1f LABEL                 # Branch if condition false
```

---

### 🧠 寄存器说明补充

|名称|说明|
|---|---|
|`$f0`–`$f31`|浮点寄存器（FPR），32 个|
|`$f0`, `$f2`, …|用于双精度需偶数寄存器配对使用（如 $f0/$f1）|

---

## ✅ 教授贴士：记忆技巧

- `.s` 表示 **single precision**（32-bit）
    
- `.d` 表示 **double precision**（64-bit）
    
- `mtc1` = **Move To Coprocessor 1**
    
- `cvt` 开头的都是 **类型转换**
    
- 比较指令 `c.xx.s` 设置一个隐藏的“浮点条件位”，搭配 `bc1t/bc1f` 跳转
    

---
