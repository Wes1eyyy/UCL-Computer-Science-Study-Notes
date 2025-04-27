
## 📘 汇编器指令速查表（Assembler Directives Quick Reference）

|中文名称|英文术语|指令格式|用途说明|示例|备注|
|---|---|---|---|---|---|
|代码段开始|Text Segment|`.text`|告诉汇编器：下面是程序代码|`.text`|必须有|
|数据段开始|Data Segment|`.data`|告诉汇编器：下面是变量数据|`.data`|必须有|
|全局符号|Global Symbol|`.globl label`|声明某标签为全局（通常是主函数）|`.globl main`|必须用于 `main`|
|字符串（带 \0）|Null-Terminated String|`.asciiz`|定义字符串并自动添加 `\0`|`.asciiz "Hello"`|常用于 `print_string`|
|字符串（不带 \0）|Raw String|`.ascii`|定义原始字符串，不添加结尾符|`.ascii "ABC"`|适合拼接|
|32位整数|Word (32-bit)|`.word`|定义一个或多个 32 位整数|`.word 5, 10, 20`|用于数组/常量|
|空空间|Space|`.space n`|分配 n 字节未初始化内存|`.space 100`|常用于 buffer|
|字节|Byte|`.byte`|定义 8 位整数（1 字节）|`.byte 0xFF, 0x10`|可用于构造结构体|
|双字|Double Word|`.double`|定义 64 位浮点数|`.double 3.1415`|浮点数据专用|
|单精度浮点|Float|`.float`|定义 32 位浮点数|`.float 3.14`|配合 `$fX` 使用|
|加载地址|Load Address|`la` (伪指令)|将标签地址加载到寄存器中|`la $a0, msg`|展开为 `lui + ori`|

---

## 🧠 使用建议：

- `.text` 和 `.data` 至少各写一次，明确结构段
    
- `.globl main` 是告诉链接器程序入口
    
- `.asciiz` 最适合用来配合 `syscall` 的字符串打印
    
- 所有 `.xxx` 指令 **不会生成机器码**，而是给**汇编器看的“提示信息”**
    

---