
# 🧠 MIPS Instruction Quick Reference

## 🧩 Common Fields in MIPS Instructions

| Field   | Full Name           | Meaning                            |
|---------|---------------------|-------------------------------------|
| `rs`    | Source Register     | First operand register              |
| `rt`    | Target Register     | Second operand / destination in I-type |
| `rd`    | Destination Register| Where the result is written         |
| `shamt` | Shift Amount        | Used in shift instructions          |
| `funct` | Function Code       | Specifies exact operation in R-type |
| `opcode`| Operation Code      | Instruction type indicator (6 bits) |

## 🧾 MIPS Instruction Types & Common Instructions

---
![[PSEUDOINSTRUCTION SET.png]]

### 🅡 R-Type

> Register-to-register operations

- **Format**: `op rs rt rd shamt funct`
    
- **Use**: 算术 / 逻辑 / 比较 / 移位
    

#### 🔧 Common Instructions:

```asm
add  $d, $s, $t     # $d = $s + $t
sub  $d, $s, $t     # $d = $s - $t
and  $d, $s, $t     # $d = $s & $t
or   $d, $s, $t     # $d = $s | $t
slt  $d, $s, $t     # $d = ($s < $t) ? 1 : 0
sll  $d, $t, shamt  # $d = $t << shamt (逻辑左移)
srl  $d, $t, shamt  # $d = $t >> shamt (逻辑右移)
sra  $d, $t, shamt  # $d = $t >> shamt (算术右移)
```
![[R-type.png]]
---

### 🅘 I-Type

> Immediate (constants), memory, branches

- **Format**: `op rs rt imm`
    
- **Use**: 加常数、存取内存、条件跳转
    

#### 🔧 Common Instructions:

```asm
addi $t, $s, imm     # $t = $s + imm
andi $t, $s, imm     # $t = $s & imm
ori  $t, $s, imm     # $t = $s | imm
lui  $t, imm         # $t = imm << 16 (装高位)

lw   $t, offset($s)  # $t = Mem[$s + offset]
sw   $t, offset($s)  # Mem[$s + offset] = $t

beq  $s, $t, label   # if $s == $t, branch
bne  $s, $t, label   # if $s != $t, branch
```

---

### 🅙 J-Type

> Jump instructions

- **Format**: `op target`
    
- **Use**: 无条件跳转，函数调用
    

#### 🔧 Common Instructions:

```asm
j   label           # Jump to label
jal label           # Jump and link (call function)
jr  $ra             # Return from function (R-type!)
```

---

### 🧠 小技巧：

- 想装一个 **32-bit 常量**：
    

```asm
lui $t0, 0x1234
ori $t0, $t0, 0x5678   # $t0 = 0x12345678
```


---
![[li,la,lw.png]]
## ✅ Notes

- All MIPS instructions are 32 bits long.
    
- R-type instructions: use `funct` to determine the specific operation.
    
- I-type: use `immediate` (16-bit constant or offset).
    
- J-type: jump to a 26-bit address (shifted by 2 bits at runtime).


---

## 完整列表：MIPS 寄存器 `$0` ~ `$31` 及其作用

|名称|编号|约定俗成用途|说明|
|---|---|---|---|
|`$zero`|`$0`|常数 0|永远是 0，不能被改写|
|`$at`|`$1`|Assembler Temporary|汇编器保留使用，程序员别动|
|`$v0-$v1`|`$2-$3`|函数返回值|用于函数的返回值|
|`$a0-$a3`|`$4-$7`|函数参数（前四个）|用于传参|
|`$t0-$t7`|`$8-$15`|临时寄存器（不需要保留）|函数内可以随意用|
|`$s0-$s7`|`$16-$23`|保存寄存器（调用者需保留）|用来存数据，调用函数时要备份|
|`$t8-$t9`|`$24-$25`|临时寄存器|额外可用的临时变量|
|`$k0-$k1`|`$26-$27`|内核保留|操作系统用，不要动|
|`$gp`|`$28`|Global Pointer|指向全局数据区，编译器使用|
|`$sp`|`$29`|Stack Pointer|栈指针，指向当前栈顶|
|`$fp`|`$30`|Frame Pointer|函数帧指针，有时也叫 `$s8`|
|`$ra`|`$31`|Return Address|函数调用返回地址（`jal` 用）|

---

## 🧠 更直观地理解这些寄存器：

|功能分类|寄存器范围|用途说明|
|---|---|---|
|常量 / 系统|`$0`, `$1`|固定值、汇编保留|
|函数通信|`$2-$7`|返回值 + 参数传递|
|临时变量|`$8-$15`, `$24-$25`|可以随意用，不用保存|
|变量存储|`$16-$23`|程序员保存的数据，用于中间结果等|
|函数控制|`$29`, `$30`, `$31`|栈操作、帧定位、返回跳转|

---

## 📌 编程时的实用建议：

- 想随便用：用 `$t0`~`$t9`，不用担心保存
    
- 想跨函数保留：用 `$s0`~`$s7`
    
- 想传参 / 返回值：用 `$a0`~`$a3`、`$v0-$v1`
    
- 栈操作记得用 `$sp`，不要手动动 `$ra` 除非你知道在干嘛

---

## 🔍 逻辑 / 位运算符对照表（中英双语）

|操作名称|英文术语|MIPS 指令|C/汇编符号|数学表达 / 含义|中文说明|
|---|---|---|---|---|---|
|与|AND (bitwise and)|`and`|`&`|`x & y`|两位都为1才为1|
|或|OR (bitwise or)|`or`|`\|`|`x \| y`|有一位为1就为1|
|异或|XOR (exclusive or)|`xor`|`^`|`x ^ y`|不同为1，相同为0|
|取反（按位）|NOT / Invert|`nor x, x, $zero` 或 `not`（伪）|`~`|`~x`|0变1，1变0|
|逻辑左移|Logical Shift Left|`sll`|`x << n`|`x × 2ⁿ`|所有位向左移，低位补0|
|逻辑右移|Logical Shift Right|`srl`|`x >> n`|`x ÷ 2ⁿ`（无符号）|高位补0|
|算术右移|Arithmetic Shift Right|`sra`|无标准符号|保留符号位向右移|保留正负号（高位补1或0）|
|设为小于|Set Less Than (Signed)|`slt`|-|`x < y → 1; else → 0`|有符号比较，小于则置1|
|设为小于(无符号)|Set Less Than Unsigned|`sltu`|-|`x < y → 1; else → 0`（无符号）|无符号比较|

---

## 🧠 记忆助攻：

- `&` → AND → All 1 才 1
    
- `|` → OR → 有 1 就 1
    
- `^` → XOR → 不一样才 1
    
- `~` → NOT → 翻转所有位
    
- `<<` → 左移 → 乘 2 的幂
    
- `>>` → 右移 → 除 2 的幂
    
- `slt` / `sltu` → 比大小置 1
    

---

## 📌 特别说明：

- `not` 不是 MIPS 硬指令，是伪指令，它被翻译为：
    
    ```assembly
    not $t0, $t1 → nor $t0, $t1, $zero
    ```
    
- `xor` 常用于：
    
    - 平均值计算：`(x & y) + ((x ^ y) >> 1)`
        
    - 交换两个值：`x ^= y; y ^= x; x ^= y;`
        

---