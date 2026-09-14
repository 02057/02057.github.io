---
layout: default
title: "task2(10)这是一张单纯的图片- 下载图片改后缀为 HTML 获取 Key"
---

# task2(10)这是一张单纯的图片：下载图片改后缀为 HTML 获取 Key

## 一、题目信息
平台：CTF靶场  
类型：web / Misc

## 二、解题思路
这类题目考察的是选手是否知道**文件真实类型与扩展名不一致**的情况。  
网页上显示为图片的文件，实际可能是一个 HTML 文件（伪装成图片），或者图片本身是用 HTML/文本方式编码的。把下载下来的文件扩展名从 `.jpg` / `.png` 改成 `.html`，再用浏览器打开，就能看到隐藏在里面的内容，从中获取 Key。

## 三、解题步骤

### 1. 下载图片
在目标网页上下载那张图片保存到本地，比如 `image.jpg`。

### 2. 查看key
在记事本中打开并ctrl+f查找key

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
