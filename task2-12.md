---
layout: default
title: "task2(12)聪明的小羊- 栅栏密码解密获取 Flag"
---

# task2(12)聪明的小羊：栅栏密码解密获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：Crypto / Misc  
题目提示：一只小羊翻过了2个栅栏  
密文：`fa{fe13f590lg6d46d0d0}`

## 二、解题思路
“翻过栅栏”提示这是**栅栏密码（Rail Fence Cipher）**，“2个栅栏”表示栏数为 2。  
栅栏密码加密时，将明文按奇偶位置交替分成两行，然后拼接成密文。解密时只需将密文从中间劈成两半，再交替读取即可还原明文。

## 三、解题步骤

### 1. 分析密文长度
密文共 22 个字符：fa{fe13f590lg6d46d0d0}
栏数为 2，因此两行各 11 个字符。

### 2. 从中间劈开
- 第一行：`fa{fe13f590`
- 第二行：`lg6d46d0d0}`

### 3. 交替拼接
依次从第一行、第二行各取一个字符：

| 步骤 | 第一行 | 第二行 | 拼接结果 |
|------|--------|--------|----------|
| 1 | f | l | f l |
| 2 | a | g | f l a g |
| 3 | { | 6 | f l a g { 6 |
| 4 | f | d | … |
| … | … | … | … |

最终得到明文：flag{6fde4163df05d900}
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
