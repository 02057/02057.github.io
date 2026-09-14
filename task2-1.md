---
layout: default
title: "Task 2 - 滑稽（查看网页源代码获取 Flag）"
---

# Task 2滑稽：查看网页源代码获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：web

## 二、解题思路
这类题目是 Web 方向最基础的入门题，考察的是选手是否知道网页源代码中可能隐藏敏感信息。  
网页在浏览器中渲染后展示的是处理过的内容，但原始 HTML 代码、注释、隐藏元素中可能包含开发者不小心留下的 Flag。

## 三、解题步骤
1. 打开目标网页。
2. 按下 `Ctrl+U` 查看网页源代码。
3. 在源代码中搜索关键词 `flag`，找到类似 `flag{...}` 的字符串，即为 Flag。
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
