---
weight: 1
layout: default
category: trackmaster
subcategory: sdk
language: cn
title: Ruby SDK
---

# TrackMaster API Ruby SDK

示例类

{:.prettyprint}
    require 'net/http'

    module TrackMasterSDK

      class Server
        def initialize(host, port = 80, options = nil)
          @host = host
          @port = port
          @options = options
        end

        def delete(uri)
          request(Net::HTTP::Delete.new(uri))
        end

        def get(uri)
          request(Net::HTTP::Get.new(uri))
        end

        def put(uri, json)
          req = Net::HTTP::Put.new(uri)
          req["content-type"] = "application/json"
          req.body = json
          request(req)
        end

        def post(uri, json)
          req = Net::HTTP::Post.new(uri)
          req["content-type"] = "application/json"
          req.body = json
          request(req)
        end

        def request(req)
          res = Net::HTTP.start(@host, @port) { |http|http.request(req) }
          unless res.kind_of?(Net::HTTPSuccess)
            handle_error(req, res)
          end
          res
        end

        private

        def handle_error(req, res)
          e = RuntimeError.new("#{res.code}:#{res.message}\nMETHOD:#{req.method}\nURI:#{req.path}\n#{res.body}")
          raise e
        end
      end
    end

### 获取access_token

    json = JSON.generate({
      client_id: "***",
      client_secret: "***",
      grant_type: "password",
      email: "***",
      password: "***"
    })

    server = TrackMasterSDK::Server.new("open.admaster.com.cn")
    response = server.post("/oauth/access_token", json)

### 获取当前用户

    server = TrackMasterSDK::Server.new("track.admasterapi.com")
    response = server.get("/user?access_token=***")

### 获取当前用户网络

    response = server.get("/user/networks?access_token=***")


