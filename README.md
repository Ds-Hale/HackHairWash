---
title: Hack HairWash
date: 2017-04-26 19:22:36
tags: [python,hairwash]
categories: 编程
---
#利用海尔洗衣逻辑漏洞达到1分洗衣效果
海尔洗衣在提交订单的时候未对价格做进一步判断，所以可以在本地修改，但是反编译apk并不能成功(未深入)，有兴趣的可以试试。
<!--more-->
洗衣的流程是先选择洗衣机--选择种类--提交订单--根据返回的价格付款--成功付款后机器运行。
进一步思考，认为还有一下攻击方法:
1. 以上提到的反编译，直接在APP写死价格，我未深入。
2. 抓包分系APP的洗衣API,直接调用发送洗衣的请求接口(未成功，不知道是不是姿势不对)。
3. 网络代理APP流量，修改返回的价格(略复杂)
我使用的是第三种。
我们hack的部分是修改返回的价格，在付款后，服务器并未对价格进行核实，仅判断是否付款，所以可以根据这个设计缺陷到达1分洗衣目的。
[项目地址](https://github.com/Ds-Hale/HackHairWash)
申明:本代码只是提供一个测试Poc,仅作为学习目的，请勿用于非法目的。