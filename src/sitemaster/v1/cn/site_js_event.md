---
weight: 7
layout: default
category: sitemaster
subcategory: site_js
language: cn
title: 自定义事件
version: v1
---

# 自定义事件

* TOC
{:toc}

自定义事件监测的前提是：必须保证站点已经添加了我们的通用代码，事件代码才能成功运行。

## 代码格式
    _smq.push(['custom', category, action, label, value, noninteraction]);

### 参数说明
* category (必填) 事件类别，要追踪事件的分类
* action (必填) 事件行为，唯一标识一个事件，命名为要监测按钮的名称
* label (可选) 事件标签，标记此事件额外的信息
* value (可选) 事件价值，标记此事件的价值
* non-interaction (可选) 非交互事件，布尔型， 具有 0 和 1 两个值。1表示：用户在跳出页如果触发了此事件，仍然算跳出。0表示：用户在跳出页如果触发了此事件，不算跳出。默认为0。
注：可选参数可以省略不填。

**注意**：
事件的 action 参数唯一标识一个事件。即，不同的事件必须具有不同的 action 名字，如果要监测事件的按钮名称都不相同，则将 action 参数命名为要监测的按钮名称，如存在相同的按钮名称，则在 action 名称上加入区分标识。

## HTML网页下自定义事件的监测  


### 调用方法

在任何需要的时候，触发以下的 js 函数即可完成对自定义事件的监测

    _smq.push(['custom',  '事件类别', '事件动作']);
    
### 调用示例

例如，若要监测帝豪网站导航菜单的点击情况（如下图）：

![](/doc/sitemaster/v1/cn/img/dihao.jpg)

原本的代码是这样的：

    <li><a href="/General/emgrand_models.html">帝豪车型</a></li>
    <li><a href=”/General/BrandStory.html”>关于帝豪</a></li>
    <li><a href=”/Article/InfoCenter/index.html”>信息中心</a></li>
 

在链接上绑定我们的监测代码，则代码如下：

    <li><a href=”/General/emgrand_models.html” onclick=”_smq.push(['custom',  '导航', '帝豪车型']);”>帝豪车型</a></li>
    <li><a href=”/General/BrandStory.html” onclick=”_smq.push(['custom',  '导航', '关于帝豪']);”>关于帝豪</a></li>
    <li><a href="/Article/InfoCenter/index.html" onclick=”_smq.push(['custom', '导航', '信息中心']);”>信息中心</a></li>

这里定义的名称和在 SiteMaster 后台的热点事件里的事件类别和事件动作相对应。类别用于对事件进行分类，动作用来唯一标识事件，不同事件具有不同的动作名称。

## Flash下自定义事件监测(AS3)


### 调用方法

Flash 中按钮被点击时，调用外部的 js进行发包，具体的参数和在HTML页面下调用相同。

不仅仅是在鼠标点击的时候，只要在需要的时候触发下面的代码，即可完成对事件的监测。例如，要监测 Flash 加载到 0% 和 50% 的次数，只需要在加载到 0% 和 50% 的时候分别触发下面的代码（自定义好类别和动作名称），在“热点事件中”即可查看对应的触发次数。

    ExternalInterface.call('_smq.push', ['custom', '类别', '动作名称']);

### 调用示例

例如，若要监测全球鹰网站首页微博和天猫旗舰店两个按钮的点击情况，按照以下步骤操作：

![](/doc/sitemaster/v1/cn/img/flash.jpg)

在Flash 中新建名为 sitemaster 的图层并选中，切换到“动作-帧（Action）”工具栏，在代码区域输入以下代码：

    import flash.events.MouseEvent;
    import flash.external.ExternalInterface;
    关注微博按钮的名称.addEventListener('click';, function(e) {
        ExternalInterface.call('_smq.push', ['custom', '首页互动', '关注微博']);
    });
    天猫旗舰店按钮的名称.addEventListener('click', function(e) {
        ExternalInterface.call('_smq.push';, ['custom', '首页互动', '天猫旗舰店']);
    });
 
代码的含义是，在用户点击关注微博按钮的时候，调用外部的 js 函数 `_smq.push(['custom','首页互动'，'关注微博'])`。不仅是点击，只要在需要的时候（比如鼠标悬停、Flash 开始加载等事件）调用这段代码即可： `ExternalInterface.call('_smq.push', ['custom', '类别', '动作名称']);`

修改保存后重新生成 flash 即可。
