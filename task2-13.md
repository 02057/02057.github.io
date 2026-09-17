---
layout: default
title: "task2(13)ok- Ook 语言解码获取 Flag"
---

# task2(13)ok：Ook 语言解码获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：Misc / Crypto  
附件：`Ook.txt`（由 `Ook.`、`Ook?`、`Ook!` 组成的文本）

## 二、解题思路
附件内容由 `Ook.`、`Ook?`、`Ook!` 三种标记组成，这是 **Ook!** 语言——一种基于 **Brainfuck** 的深奥编程语言。  
Ook! 每两个标记组合成一个 Brainfuck 指令，按规则翻译后运行，即可输出 Flag。

### Ook! 与 Brainfuck 的对应关系

| Ook! 标记对 | Brainfuck 指令 | 含义 |
|-------------|----------------|------|
| `Ook. Ook.` | `+` | 当前单元格加 1 |
| `Ook! Ook!` | `-` | 当前单元格减 1 |
| `Ook. Ook?` | `>` | 指针右移 |
| `Ook? Ook.` | `<` | 指针左移 |
| `Ook! Ook.` | `.` | 输出当前字符 |
| `Ook. Ook!` | `,` | 输入 |
| `Ook! Ook?` | `[` | 循环开始 |
| `Ook? Ook!` | `]` | 循环结束 |

## 三、解题步骤

### 1. 将 Ook 翻译为 Brainfuck
使用 Python 脚本把 Ook 文本转换成 Brainfuck 代码：

import re
with open('Ook.txt', 'r', encoding='utf-8') as f:
    text = f.read()
mapping = {
    'Ook. Ook.': '+',
    'Ook! Ook!': '-',
    'Ook. Ook?': '>',
    'Ook? Ook.': '<',
    'Ook! Ook.': '.',
    'Ook. Ook!': ',',
    'Ook! Ook?': '[',
    'Ook? Ook!': ']',
}
tokens = re.findall(r'Ook[.?!]', text)
bf = ''
for i in range(0, len(tokens) - 1, 2):
    key = tokens[i] + ' ' + tokens[i+1]
    if key in mapping:
        bf += mapping[key]
def run_bf(code):
    tape = [0] * 30000
    ptr = 0
    pc = 0
    output = ''
    stack = []
    bracket_map = {}
    # 预计算括号匹配
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
            pass  # 本题不需要输入
        elif c == '[':
            if tape[ptr] == 0:
                pc = bracket_map[pc]
        elif c == ']':
            if tape[ptr] != 0:
                pc = bracket_map[pc]
        pc += 1
    return output
print(run_bf(bf))

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
