---
layout: default
title: "task2(6)GET - URL 参数传入 what=flag 获取 Flag"
---

# task2(6)GET：URL 参数传入 what=flag 获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：web

## 二、解题思路
这类题目考察是否知道 **URL 查询参数（Query String）** 可能影响服务器返回内容。  
有些题目会故意留一个参数接口，当传入特定参数时，服务器会返回 Flag。常见形式是 `?what=flag` 或 `?flag=1` 等。我们需要手动在 URL 后面添加参数，触发服务器返回 Flag。

## 三、解题步骤
1. 打开目标网页，发现直接给予源代码
2. 在浏览器地址栏的 URL 末尾添加 `?what=flag`。
3. 按回车访问，页面会返回 Flag。
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
