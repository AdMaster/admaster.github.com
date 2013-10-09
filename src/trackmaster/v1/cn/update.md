---
weight: 20
layout: default
category: trackmaster
language: cn
title: 更新
---

# 更新

* TOC
{:toc}

## 代理接口/文档更新 

<table width="560" border="0" bordercolor="#000000">
  <tr>
    <td width="94"><div align="center"><strong>更新时间</strong></div></td>
    <td width="456"><div align="center"><strong>详细说明</strong></div></td>
  </tr>
    <tr>
    <td>2013-08-07</td>
    <td>变更项目报告中维度（dims）选择地域（geo）名称为province。原geo并行一段时间。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/campaign_report.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-08-06</td>
    <td>由于业务需求，去除按 IP 去重的所有相关指标。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/campaign_report.html">查看详细</a></td>
  </tr>
    <tr>
    <td>2013-06-20</td>
    <td>更改购买量的数据类型为float，点位的购买量支持录入小数。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/spot.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-08</td>
    <td>广告位信息补充为同时显示频道名称和频道 ID。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-07</td>
    <td>修改“获取指定广告位下关键字监测代码”接口路由地址。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/code.html#section-2">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-05</td>
    <td>广告位信息中广告位频道 ID 改为显示广告位频道名称。广告位列表中不再提供频道信息，由广告位详情统一提供。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-04</td>
    <td>“获取指定工作网络下所有广告主属性列表”增加可以针对网络广告主别名进行模糊搜索功能。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertiser.html#section-3">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-04</td>
    <td>“获取指定工作网络下媒体库列表”增加可以针对网络媒体名称和媒体域名进行模糊搜索功能。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/media.html#section-3">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-04</td>
    <td>添加“获取项目下监测代码”接口。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/code.html#section-3">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-27</td>
    <td>添加“批量修改广告位下点位”接口。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/spot.html#section-3">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-27</td>
    <td>调整创意属性。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/creative.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-27</td>
    <td>调整频道属性及广告位属性、创建广告位时频道为广告位的可选项。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/placement.html#section-3">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-20</td>
    <td>添加“获取指定广告位下的关键字监测代码”接口。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/code.html#section-2">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-18</td>
    <td>添加 page 和 per_page 参数到各获取列表的接口中，在使用获取列表的接口时，可以使用分页功能。</td>
  </tr>
  <tr>
    <td>2013-02-17</td>
    <td>修改创建项目时传入的目标受众人群的性别格式。
如仅选择一个性别，格式为"sex": ["female"]；如选择同时选择“男”和“女”，格式为"sex": ["male","female"]；如不选择性别，则不输入"sex"内容，即{ "age": "19-25"}。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/campaign.html#section-3">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 C# SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/cs.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 Java SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/java.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 Node.js SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/nodejs.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-04</td>
    <td>添加 PHP SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/php.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-01</td>
    <td>添加 Python SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/python.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-01</td>
    <td>添加 Ruby SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/ruby.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-01-25</td>
    <td>获取项目报告时如时间粒度选择“小时”(time=hourly)，开始时间和结束时间(start_time、end_time)的格式为 YYYY-MM-DDThh:mm:ss+08:00，输出时间格式为 YYYY-MM-DDThh:mm:ss+08:00。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/campaign_report.html#section-1">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-01-16</td>
    <td>创建项目时同广告主下项目不能重名。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/campaign.html#section-3">查看详细</a></td>
  </tr>
  <tr>
  	<td>2013-01-09</td>
	<td>获取地域信息时对应英文名称。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/territory.html">查看详细</a></td>
  </tr>
</table> 


## 媒体接口/文档更新    

<table width="560" border="0" bordercolor="#000000">
  <tr>
    <td width="94"><div align="center"><strong>更新时间</strong></div></td>
    <td width="456"><div align="center"><strong>详细说明</strong></div></td>
  </tr>
      <tr>
    <td>2013-10-09</td>
    <td>添加IES新接口，即日起新接入IES的对接方使用此新接口。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/media_report.html#ies.html">查看详细</a></td>
  </tr>
    <tr>
    <td>2013-08-06</td>
    <td>由于业务需求，去除按 IP 去重的所有相关指标。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/media_report.html#section-5">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-08</td>
    <td>广告位信息补充为同时显示频道名称和频道 ID。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/publisher_placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-05</td>
    <td>广告位信息中广告位频道 ID 改为显示广告位频道名称。广告位列表中不再提供频道信息，由广告位详情统一提供。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/publisher_placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-27</td>
    <td>调整广告位和频道属性。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/publisher_placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 C# SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/cs.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 Java SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/java.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 Node.js SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/nodejs.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-04</td>
    <td>添加 PHP SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/php.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-01</td>
    <td>添加 Python SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/python.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-01</td>
    <td>添加 Ruby SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/ruby.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-01-25</td>
    <td>获取项目报告时如时间粒度选择“小时”(time=hourly)，开始时间和结束时间(start_time、end_time)的格式为 YYYY-MM-DDThh:mm:ss+08:00，输出时间格式为 YYYY-MM-DDThh:mm:ss+08:00。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/media_report.html#section-5">查看详细</a></td>
  </tr>
  <tr>
  	<td>2013-01-09</td>
	<td>获取地域信息时对应英文名称。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/publisher_territory.html">查看详细</a></td>
  </tr>
</table>    



## 广告主接口/文档更新    

<table width="560" border="0" bordercolor="#000000">
  <tr>
    <td width="94"><div align="center"><strong>更新时间</strong></div></td>
    <td width="456"><div align="center"><strong>详细说明</strong></div></td>
  </tr>
      <tr>
    <td>2013-08-06</td>
    <td>由于业务需求，去除按 IP 去重的所有相关指标。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_report.html#section-1">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-08</td>
    <td>广告位信息补充为同时显示频道名称和频道 ID。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-05</td>
    <td>广告位信息中广告位频道 ID 改为显示广告位频道名称。广告位列表中不包含频道信息，由广告位详情统一提供。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-04</td>
    <td>调整创意属性。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_creative.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-03-04</td>
    <td>调整广告位属性。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_placement.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-17</td>
    <td>项目信息中的目标受众人群的性别格式更改为数组形式。请查看“获取指定广告主的项目”和“获取指定项目信息”接口中
"target_audience"信息。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_campaign.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 C# SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/cs.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 Java SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/java.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-16</td>
    <td>添加 Node.js SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/nodejs.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-04</td>
    <td>添加 PHP SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/php.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-01</td>
    <td>添加 Python SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/python.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-02-01</td>
    <td>添加 Ruby SDK 示例说明。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/sdk/ruby.html">查看详细</a></td>
  </tr>
  <tr>
    <td>2013-01-25</td>
    <td>获取项目报告时如时间粒度选择“小时”(time=hourly)，开始时间和结束时间(start_time、end_time)的格式为 YYYY-MM-DDThh:mm:ss+08:00，输出时间格式为 YYYY-MM-DDThh:mm:ss+08:00。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_report.html#section-1">查看详细</a></td>
  </tr>
  <tr>
  	<td>2013-01-09</td>
	<td>获取地域信息时对应英文名称。<a href="http://dev.admaster.com.cn/doc/trackmaster/v1/cn/advertisers_territory.html">查看详细</a></td>
  </tr>
</table>   