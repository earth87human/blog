---
title: 如何在 Cisco 裝置設定 inter VLAN routing
date: 2023-08-01
slug: inter-vlan-routing
tags: 
    - Router
    - VLAN
categories:
    - Network
---

## 三種 inter VLAN routing 的方法 : 

> 1 . 每個 VLAN 在 Switch / Router 上各自擁有獨立的物理街口，並設置成 Access Port。

> 2 . Switch / Router 之間用 Trunk 連接 , 所有 VLAN 跑在同一條網線上。

> 3 . 使用 Layer 3 Swtich , 設定 SVI 接口。

![inter vlan routing](step-1-1.png)