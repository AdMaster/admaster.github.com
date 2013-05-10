---
weight: 7
layout: default
category: sitemaster
subcategory: site_js
language: cn
title: 虚拟页面
---

# 虚拟页面

* TOC
{:toc}

自定义虚拟页面监测的前提是：必须保证站点已经添加了我们的通用代码，监测代码才能成功运行。

## HTML网页下虚拟页面监测



### 应用场景

虚拟页面与常规的 PV 在指标上没有区别，都会有浏览量、页面停留时间等指标。唯一的区别是，虚拟页面的加载不会自动执行我们的监测代码，需要手动添加调用。

什么是虚拟页面？

例如，点击某个按钮后弹出一个悬浮层：

![](/doc/sitemaster/v1/cn/img/tanchuang.png)

或者，点击一个按钮后页面大部分内容进行 Ajax 局部刷新（像点击QQ空间左侧导航栏的效果，URL不变，但是主体内容改变了）：

![](/doc/sitemaster/v1/cn/img/qzone.png)

这时候就需要部署虚拟页面的代码进行监测，我们只需将监测的代码绑定到按钮的 click 事件上即可，代码介绍如下：

### 调用方法

    _smq.push(['pageview', path, title]);

### 参数说明

* path (必选) 页面路径，不包含协议和 host 的 url ,以斜杠开始，例如，“http://www.abc.com/welcome?uid=1293” 则写成 “/welcome?uid=1293”
* title (必选) 页面标题，不选则默认为当前页面真实的标题

### 调用示例
    
     
      <a href="#" onclick="_smq.push(['pageview', '/path', '虚拟页面标题']);">这是虚拟页面</a>
 


## Flash下虚拟页面监测（AS3）

### 应用场景

Flash 下虚拟页面的监测比静态 html 下虚拟页面更加常用，Flash 网站用不同的 Flash 场景替代网页，用户在切换时网页时并不重新加载页面，所以每次场景的切换都需要设定虚拟页面的监测。

例如，奥迪网站通过点击底部的导航按钮进行页面切换，这是一个大的 Flash，点击导航按钮页面并不刷新，需要在每个按钮上添加虚拟页面监测的代码。如下图：

![](/doc/sitemaster/v1/cn/img/aodi.png)

### 调用方法

Flash 中场景切换时，调用外部的  js 进行发包，具体的参数和在 HTML 页面下调用相同,只需要在需要的场景下触发以下的代码即可：

    ExternalInterface.call('_smq.push', ['pageview', '/path1', '虚拟页面标题1']);

需要注意的是，在触发这句代码之前，需要引入 `ExternalInterface`,通过如下代码引入：

    import flash.external.ExternalInterface;
    
### 调用示例

在 Flash 中新建名为 sitemaster 的图层并选中，切换到“动作-帧（Action）”工具栏，在代码区域输入以下代码：

    import flash.events.MouseEvent;
    import flash.external.ExternalInterface;
    页面切换按钮的名称.addEventListener('click', function(e) {
        ExternalInterface.call('_smq.push', ['pageview', '/path1', '虚拟页面标题1']);
    });

`页面切换按钮的名称`指要绑定该事件按钮的名称( name )，保存后重新生成 flash 即可。
