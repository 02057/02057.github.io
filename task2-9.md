---
layout: default
title: "task2(9)瑞士军刀- nc 连接获取 Flag"
---

# task2(9)瑞士军刀：nc 连接获取 Flag

## 一、题目信息
平台：CTF靶场  
类型：Pwn  
连接地址：`nc 160.202.254.160 16040`

## 二、解题思路
题目提供一个 TCP 服务，需要使用 `netcat`（nc）连接。Windows 默认不带 `nc` 命令，可以使用 Python 的 `socket` 库代替。连接后观察服务器返回内容，可能需要交互输入，最终获取 Flag。

## 三、解题步骤

### 1. 使用 Python 连接（代替 nc）
新建 `task2-9.py`，输入以下代码：
import socket
host = "160.202.254.160"
port = 16040
s = socket.socket()
s.connect((host, port))
s.send(b"cat flag\n")
print(s.recv(4096).decode(errors="ignore"))
data = s.recv(4096)
print(data.decode(errors="ignore"))
s.close()
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
