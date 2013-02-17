---
weight: 1
layout: default
category: trackmaster
subcategory: sdk
language: en
title: Node.js SDK
---

# TrackMaster API Node.js SDK

### API Sample

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

### Get an access_token

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

### Get the user

{:.prettyprint}
    var client = new TrackmasterClient("track.admasterapi.com");
    client.get("/user?access_token=***", callback);

### Get the network of user in TrackMaster

{:.prettyprint}
    client.get("/user/networks?access_token=***", callback);


