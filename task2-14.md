---
layout: default
title: "task2(14)[+-<>]- Brainfuck 解码获取 Flag"
---

# task2(14)[+-<>]：Brainfuck 解码获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：Misc / Crypto  
题目提示：请输入flag  
附件：一段由 `+ - < > [ ] . ,` 组成的代码

## 二、解题思路
题目给出的代码只包含 `+`、`-`、`<`、`>`、`[`、`]`、`.`、`,` 这 8 种符号，这是典型的 **Brainfuck** 语言。  
Brainfuck 是一种极简的图灵完备语言，只有 8 个指令，通过操作一个指针和一条"纸带"（数组）来完成计算。我们需要用解释器运行这段代码，输出结果即为 Flag。

### Brainfuck 指令表

| 指令 | 含义 |
|------|------|
| `>` | 指针右移 |
| `<` | 指针左移 |
| `+` | 当前单元格加 1 |
| `-` | 当前单元格减 1 |
| `.` | 输出当前单元格字符 |
| `,` | 输入一个字符到当前单元格 |
| `[` | 若当前单元格为 0，跳转到对应的 `]` |
| `]` | 若当前单元格不为 0，跳转到对应的 `[` |

## 三、解题步骤

### 1. 识别 Brainfuck 代码
只含 8 种符号，去掉空格和换行后即为 Brainfuck 源码。

### 2. 使用 Python 解释器运行
新建 `bf.py`，粘贴以下代码：

```python
# Brainfuck 解释器
def run_bf(code):
    tape = [0] * 30000
    ptr = 0
    pc = 0
    output = ''
    stack = []
    bracket_map = {}
    for i, c in enumerate(code):
        if c == '[':
            stack.append(i)
        elif c == ']':
            j = stack.pop()
            bracket_map[i] = j
            bracket_map[j] = i
    while pc < len(code):
        c = code[pc]
        if c == '>':
            ptr += 1
        elif c == '<':
            ptr -= 1
        elif c == '+':
            tape[ptr] = (tape[ptr] + 1) % 256
        elif c == '-':
            tape[ptr] = (tape[ptr] - 1) % 256
        elif c == '.':
            output += chr(tape[ptr])
        elif c == ',':
            pass
        elif c == '[':
            if tape[ptr] == 0:
                pc = bracket_map[pc]
        elif c == ']':
            if tape[ptr] != 0:
                pc = bracket_map[pc]
        pc += 1
    return output

# 题目给出的 Brainfuck 代码
bf_code = """
+++++ +++++ [->++ +++++ +++<] >++.+ +++++ .<+++ [->-- -<]>- -.+++ +++.< ++++[ ->+++ +<]>+ +++.< +++++ +++[- >---- ----< ]>--- ----- ---.< +++++ ++[-> +++++ ++<]> +++.< +++++ +[->- ----- <]>-- ----- -.--. ----. --.++ +++++ +.<++ ++++[ ->+++ +++<] >++++ +.++. <++++ ++[-> ----- -<]>- ----- ----. -.<++ +++++ [->++ +++++ <]>+. ----. ++++. <++++ +++[- >---- ---<] >---- .+.<+ +++++ ++[-> +++++ +++<] >++++ +++++ ++.<
"""

# 清理代码：只保留 Brainfuck 的 8 个有效字符
clean_code = ''.join(c for c in bf_code if c in '+-<>[].,')

# 运行并打印结果
print(run_bf(clean_code))
<div style="text-align: center; margin-top: 40px;">
  <a href="/" style="
    display: inline-block;
    padding: 12px 24px;
    background-color: #2563eb;
    color: white;
    text-decoration: none;
    border-radius: 8px;
    font-size: 16px;
    font-weight: bold;
  ">
    ← 返回首页
  </a>
</div>
