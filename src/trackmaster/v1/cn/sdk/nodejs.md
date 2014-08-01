---
weight: 1
layout: default
category: trackmaster
subcategory: sdk
language: cn
title: Node.js SDK
version: v1
---

# TrackMaster API Node.js SDK

{:.prettyprint}
    (function() {
      var TrackmasterClient, http;

      http = require('http');

      TrackmasterClient = (function() {

        function TrackmasterClient(host, port) {
          if (port == null) {
            port = 80;
          }
          this.host = host;
          this.port = port;
          this.error = null;
        }

        TrackmasterClient.prototype.get = function(path, callback) {
          return this.req("GET", path, null, callback);
        };

        TrackmasterClient.prototype.post = function(path, data, callback) {
          return this.req("POST", path, data, callback);
        };

        TrackmasterClient.prototype.put = function(path, data, callback) {
          return this.req("PUT", path, data, callback);
        };

        TrackmasterClient.prototype["delete"] = function(path, callback) {
          return this.req("DELETE", path, null, callback);
        };

        TrackmasterClient.prototype.req = function(method, path, data, callback) {
          var options, req;
          options = {
            hostname: this.host,
            port: this.port,
            path: path,
            method: method
          };
          req = http.request(options, callback);
          req.on("error", function(e) {
            return this.error = e;
          });
          if (data) {
            req.write(data);
          }
          return req.end();
        };

        return TrackmasterClient;

      })();

    }).call(this);

### 获取access_token

{:.prettyprint}
      var json = JSON.stringify({
        "client_id": "***",
        "client_secret": "***",
        "grant_type": "password",
        "email": "***",
        "password": "***"
      });

      var callback = function(res) {
        console.log("STATUS: " + res.statusCode);
        console.log("HEADERS: " + JSON.stringify(res.headers));
        res.setEncoding("utf8");
        return res.on("data", function(chunk) {
          return console.log("BODY: " + chunk);
        });
      };

      var client = new TrackmasterClient("open.admaster.com.cn");
      client.post("/oauth/access_token", json, callback);

### 获取当前用户

{:.prettyprint}
    var client = new TrackmasterClient("track.admasterapi.com");
    client.get("/user?access_token=***", callback);

### 获取当前用户网络

{:.prettyprint}
    client.get("/user/networks?access_token=***", callback);


