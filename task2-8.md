---
layout: default
title: "task2(8)GIT- .git 泄露获取 Flag"
---

# task2(8)GIT：.git 泄露获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：web

## 二、解题思路
这类题目考察是否知道 **`.git` 目录泄露** 漏洞。  
网站在部署时如果没有删除 `.git` 文件夹，攻击者就可以直接访问 `http://靶场/.git/`，下载整个 Git 仓库的元数据，进而恢复网站源代码、查看历史提交记录，从中找到 Flag 或敏感信息。

本题的 Flag 并没有直接出现在源码文件里，而是藏在 `.git/objects` 目录下的**压缩对象**中，通过 Python 脚本暴力解压所有对象找到。

## 三、解题步骤

### 1.安装git-dumper
    CMD中安装git-dumper

### 2.python 下载仓库并解压
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
