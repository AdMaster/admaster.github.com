---
weight: 1
layout: default
category: trackmaster
language: cn
title: 文件上传下载DEMO
---
<script src="/doc/assets/js/jquery-1.8.3.js"></script>
<script src="/doc/assets/js/jquery.ui.widget.js"></script>
<script src="/doc/assets/js/jquery.iframe-transport.js"></script>
<script src="/doc/assets/js/jquery.fileupload.js"></script>
<script>

$(function () {
   var string =location.search;
   var exp = /access_token=([a-zA-Z0-9]{40})/.exec(string);

   var token = (exp !== null)? exp[1] :"";

   var baseUrl = "http://58.215.168.154:8080/";
   var upUrl = baseUrl + "files?access_token="+token;
   var downUrl = baseUrl + "files/";

   document.getElementById('fileupload1').addEventListener('change', function(e) {
     var file = this.files[0];
     var xhr = new XMLHttpRequest();
     var formData = new FormData();
     formData.append("thefile", file);
     xhr.open('post', upUrl, true);
     xhr.send(formData);
     xhr.onload = function(event) {
       id = JSON.parse(event.target.response).id;
       document.getElementById('up1id').href = downUrl + id; };
     }, false);

   $("#fileupload2").attr('data-url',upUrl);
   $('#fileupload2').fileupload({
     dataType: 'json',
     done: function (e, data) {
      $('#up2id').attr("href",downUrl + data.result.id);
      }
    });

});
</script>

# 文件上传下载API

## 上传文件

    POST /files

**参数**
`access_token`
: _必选_ 从open.admaster.com.cn获取到的access_token

**响应**

{:.prettyprint}
    {
     "id":"1",//即下载时用到的file_id
     "name":"0.gif",
     "size":100,
     "created_at":"2013-01-01T00:00:00+08:00",
     "is_img":true,
     "type":"image/gif"
    }

## 下载文件

    GET /files/:file_id

**参数**
`width`
: _可选_ 图像宽度，默认为100

`height`
: _可选_ 图像高度，默认为100

# 示例

## 请先 [登录](http://open.admaster.com.cn/oauth/authorize?client_id=0e452b3ab685e1e2b109&response_type=token)，登录后同意访问您的数据，会回到本页面（已得到access_token）

## 点击"Choose Files"上传文件后，点击"下载链接"可访问刚上传的文件

## 公用javascript变量

{:.prettyprint}
    var baseUrl = "http://58.215.168.154:8080/";
    var upUrl = baseUrl + "files?access_token="+token;
    var downUrl = baseUrl + "files/";

### 例1.不使用jquery
<input id="fileupload1" type="file" name="files[]" data-url="" multiple><a id="up1id">下载链接</a>

html代码

{:.prettyprint}
    <input id="fileupload1" type="file" name="files[]" data-url="" multiple><a id="up1id">下载链接</a>

javascript代码

{:.prettyprint}
    document.getElementById('fileupload1').addEventListener('change', function(e) {
      var file = this.files[0];
      var xhr = new XMLHttpRequest();
      var formData = new FormData();
      formData.append("thefile", file);
      xhr.open('post', upUrl, true);
      xhr.send(formData);
      xhr.onload = function(event) {
        id = JSON.parse(event.target.response).id;
        document.getElementById('up1id').href = downUrl + id; };
      }, false);


### 例2.使用[jQuery File Upload插件（基本设置）](https://github.com/blueimp/jQuery-File-Upload/wiki/Basic-plugin)
<input id="fileupload2" type="file" name="files[]" data-url="" multiple><a id="up2id">下载链接</a>

javascript代码

{:.prettyprint}
    $("#fileupload2").attr('data-url',upUrl);
       $('#fileupload2').fileupload({
         dataType: 'json',
         done: function (e, data) {
          $('#up2id').attr("href",downUrl + data.result.id);
          }
        });

### 更多效果请参考[jquery File upload](https://github.com/blueimp/jQuery-File-Upload/wiki)
