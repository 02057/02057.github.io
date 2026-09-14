---
layout: default
title: "task2(7)post- Python POST 获取 Flag"
---

# task2(7)post：Python POST 获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：web

## 二、解题思路
这类题目考察是否知道如何**用 Python 发送 POST 请求**，通过提交特定参数来获取 Flag。  
网页可能只接受 POST 请求，或者需要提交表单数据（如 `what=flag`），用浏览器直接访问无法触发。我们需要用 Python 的 `requests` 库构造 POST 请求，把参数放在请求体中发送，从服务器返回的内容里找到 Flag。

## 三、解题步骤

### 1. 安装 requests 库
打开命令提示符（cmd），输入：
pip install requests
### 2.python post 得到flag
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
