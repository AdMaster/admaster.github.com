---
weight: 7
layout: default
category: sitemaster
language: cn
title: 代码部署
version: v1
---

# 代码部署

* TOC
{:toc}


## 通用代码
新建站点之后，系统会生成类似如下的一段监测代码：


    <script type="text/javascript">
      var _smq = _smq || [];
      _smq.push(['_setAccount', 'F3AB35AB', new Date()]);
      _smq.push(['_setDirectoryIndex', 'index.html']);
      _smq.push(['pageview']);    

      (function() {
      var sm = document.createElement('script'); sm.type = 'text/javascript'; sm.async = true;
      sm.src = ('https:' == document.location.protocol ? 'https://' : 'http://') + 'cdnmaster.com/sitemaster/sm.js';
      var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(sm, s);
      })();
    </script>

您需要把系统生成的代码部署在网站的所有页面上，以保证所有页面的浏览行为都能够被采集到。如果需要针对特定的按钮和行为进行监测，则需要单独部署[自定义事件](/doc/sitemaster/v1/cn/site_js_event.html)代码或[虚拟页面](/doc/sitemaster/v1/cn/site_js_pageview.html)的代码。