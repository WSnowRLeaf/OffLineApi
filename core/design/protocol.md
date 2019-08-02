# 联动服务商API接入文档

![内部调用关系图](..\..\assets\img\trans\queryOrder\innerRela.png)



```mermaid
graph TB
entry1(传入参数) --> core1(调用交易查询接口)
core1 --> comp1{调用基础鉴权接口}
comp1 --> comp1_1[商户状态鉴权]
comp1_1 --> comp1_2[代理商状态鉴权]
comp1_2 --> comp1_3[商户代理商匹配鉴权]
comp1_3 --> comp1_4[终端有效性鉴权]
comp1_4 -->|Un| core5_1[立码付处理器]
comp1_4 -->|AL| core5_2[支付宝处理器]
comp1_4 -->|WX| core5_3[微信处理器]
comp1_4 -->|YL| core5_4[银联处理器]
req1(传入参数) --> C{分支}
C -->|One| D[Result one]
C -->|Two| E[Result two]

```



```sequence
title: 时序图
participant 前置服务 as a
participant 核心服务 as b
participant 鉴权服务 as c
participant POSP as d

a -> b: 调用交易查询接口
b -> c: 调用商户鉴权接口
c -> c: 商户状态鉴权
c -> c: 代理商状态鉴权
c -> c: 商户代理商匹配鉴权
c -> c: 终端有效性鉴权
c -- b: 基础鉴权校验
b -- b: 商户订单号鉴权
```



