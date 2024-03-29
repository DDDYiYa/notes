# 洪涝

---

## 大致思路

我们会获得一些设备的状态，其中包括一些设备的故障信息。根绝这些故障信息，结合判断当时当地的气象信息，进行极端天气预警。

## 后端

### 后端框架

**Framework23**
实现了连续错误登录禁止，和超时终止会话功能。

1. 配合里面example.sql数据库使用。
1. 里面需要先理解的地方, auth.py中的login，和method.py中的permission。

## 数据

### 自己假设一些数据

1. 气象数据没有，先自己产生一些设备故障信息，然后前端实现这些信息的增删改查。
1. 然后按照其他的系统的界面，做一些统计功能。

### 设备故障信息

1. 断路器跳闸故障
2. 工控机（监视器）故障
3. 母线过欠压
4. 蓄电池熔丝熔断
5. 绝缘老化
6. 蓄电池故障
7. 交流单元设备故障
8. 开关量单元故障
9. 直流接地故障
10. 开关分合及控制器故障
11. 继电保护故障
12. 灯光照明故障
13. 通讯故障
14. 直流分支信号弱

### 设备运行参数

1. 电压
2. 功率

## 前端

**安装 Angular**
需要安装 node.js, typescript，typings，ts-node，Angular。

1. 安装node.js
1. 安装 Angular
``$ npm install -g @angular/cli``

**安装 Angular 组件库 NG-ZORRO**
进入项目文件夹，执行以下命令后将自动完成 ng-zorro-antd 的初始化配置，包括引入国际化文件，导入模块，引入样式文件等工作。
``$ ng add ng-zorro-antd``

## 我遇到的问题

### 1.  ``$ ng add ng-zorro-antd`` 装了4个小时也没完？

### 2. 变电站故障信息有哪些？

分别是：系统故障、母线过欠压、交流故障、馈线开关跳闸、蓄电池熔丝熔断、绝缘故障（例如直流接地故障、绝缘老化）、模块故障、蓄电池故障、工控机（监视器）故障、单元设备故障（交流单元、直流单元、开关量单元，这些设备通常用一个单独24kv的供电设备供电）、直流故障（直流接地故障、电阻增大、开关分合及控制、继电保护、灯光照明、通讯、直流分支信号弱）、设备老化（绝缘老化、零件老化）。
**变电站内的主要设备**

1. 一次设备
一次设备指直接生产、输送、分配和使用电能的设备，主要包括变压器、高压断路器、隔离开关、母线、避雷器、电容器、电抗器等。
2. 二次设备
变电站的二次设备是指对一次设备和系统的运行工况进行测量、监视、控制和保护的设备，它主要由包括继电保护装置、自动装置、测控装置、计量装置、自动化系统以及为二次设备提供电源的直流设备。

<http://www.hntpyxl.com/articles/35kvbd.html>

**1. 电磁干扰故障**
将研究对象锁定为66kV变电站,其受电磁干扰出现的故障一般有两类,一种来源于外部,另一种则是源于内部。外部电磁干扰通常无法，只能尽量的减缓，*它的表现形式为短路故障、雷电天气等*。反观内部电磁干扰，它指的就是系统内部零件异常而出现的干扰，又或者是结构没有问题，但是由于突然断电、通电的那一刹那造成的干扰。
**2. 断路器跳闸故障**
变电站设备一般会发生各种各样的问题，其中继电器跳闸就是主要问题之一。它不但会造成母线失压，情况更甚的还将造成整个变电站综合保护系统的损毁，这对66kV变电站来说无疑是灭顶之灾，成本损失极为严重。对事故分析之后发现，继电器跳闸情况一般有三大类:

- 继电器本身发生故障，保护指令运行受阻，进而发生的跳闸加大了故障影响程度。
- 监控系统的问题，继电器在没有监控的情况下传出跳闸指令,造成了严重的跳闸事故。
- 在系统正常运行的工况下，开关出现质量问题，不能实现正常的开闭,继而造成跳闸。

**3. 电缆线路故障**
只要是发生电缆线路的故障,无论是何种事故,无论情况的大小,都将为供电系统埋下安全隐患.为66kV变电站带来大量的问题，经常发生的故障如下。

1. 电线电缆的质量参差不齐
电线电缆质量的优劣程度将直接决定其运行时的故障发生率,一旦在电线电缆中掺入杂质、废气与汗液,那么在运营时,这些外来物质会在电场作用下，产生不必要的树枝放电情况。除此之外，电线电缆在开始接线或者运营之后，只要出现接触不良问题就会产生多余的发热，长期如此，绝缘层势必会发生老化,更有甚者还会直接击穿绝缘层.导致短路现象的产生,这不但会影响着自身,而且还会危及系统内部其他的并行线路。
2. 电线电缆终端金属屏蔽接地问题
通常状况下，电线电缆上与大地连接的部分一般有两处，用于接地的电阻值通常都比规定电阻要小，只有这样电压才能受到合理的调控，电缆的安全性才能有保障。不过，如果该部分出现问题，那么电路中就会出现较高的电压，进而腐化电路中的绝缘部分，使得电缆的正常运营受到不利影响。
3. 电线电缆的安装问题
在进行电线电缆的铺设时，十分有必要在底层加上软土和砂砾,然后再加一层盖板,这是为了防止运营过程中电线电缆功能部分受到重物的压迫，致使其产生机械外伤，进而不利于66kV变电站的运营。
4. 电线电缆负荷的问题
政府出台政策法规表明，电线电缆在正常工况下适宜的温度为25摄氏度。不仅如此，还要严格的把控电缆的载流量，使其在正常范围内。在夏天室温通常会变得异常之高，一旦防护措施出现纰漏，同样会造成电线电缆的老化。
