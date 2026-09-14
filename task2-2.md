---
layout: default
title: "Task 2(2)：计算器 - Ctrl+U 查看 JS 获取 Flag"
---

# Task 2(2)：计算器 - Ctrl+U 查看 JS 获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：web

## 二、解题思路
这类题目是 Web 方向最基础的入门题，考察的是选手是否知道网页源代码中可能隐藏敏感信息。  
网页在浏览器中渲染后展示的是处理过的内容，但原始 HTML 代码中引用的外部 JS 文件里，也可能包含开发者不小心留下的 Flag。

## 三、解题步骤
1. 打开目标网页（计算器页面）。
2. 按下 `Ctrl+U` 查看网页源代码。
3. 在源代码中找到类似 `<script src="js/code.js"></script>` 的引用。
4. 点击 `js/code.js` 链接，或直接在地址栏访问 `http://靶场地址/js/code.js`。
5. 在打开的 JS 文件中搜索关键词 `flag`，找到类似 `flag{...}` 的字符串，即为 Flag。
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
