---
title: 如何在 Cisco Switch 裝置設定 line console 登入密碼
date: 2023-02-01
tags: 
    - switch
categories:
    - Network
---

## 需求 : 

>  在 Cisco Switch 裝置設定 line console 登入密碼，防止不肖人士登入。

## Step 1  : 建立模擬環境

> 開啟 Packet Tracer 建立模擬環境，如下圖

![模擬環境](packet-tracer.png)

## Step 2  : 設定密碼

> 打開 Switch CLI 設定密碼

```c++
# 進入 privileged mode
Switch> enable
# 進入 config mode
Switch# configure termianl
# 關閉 dns lookup
Switch(config)# no ip domain-lookup
# 選擇 line console 0 , switch 只有一個 console port 故選擇 0
Switch(config)# line console 0
# 設定密碼
Switch(config-line)# password earth87human
# 啟用密碼
Switch(config-line)# login
```

## Step 3  : 設定逾時自動登出

> 打開 Switch CLI 設定逾時自動登出

```c++
# 設定逾時自動登出
Switch(config-line)# exec-time 02 30  設定逾時時間為2:30
```

## Step 4  : 驗證

> 驗證 Laptop 是否可以用密碼登入 Switch 

![選取 Terminal](step-4-1.png)

![按 OK](step-4-2.png)

![輸入密碼](step-4-3.png)

![成功連線](step-4-4.png)

## Step 5  : 取消登入密碼

> 打開 Switch CLI 取消登入密碼

```c++
# 取消登入密碼
Switch(Config)# line console 0
Switch(Config-line)# no password  
```

## 大功告成～