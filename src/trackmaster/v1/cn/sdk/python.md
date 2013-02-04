---
weight: 3
layout: default
category: trackmaster
subcategory: sdk
language: cn
title: Python SDK
---

# TrackMaster API Python SDK

### 示例类

{:.prettyprint}
    import httplib, json

    class TrackMasterSDK:

        def __init__(self, host, port=80, options=None):
            self.host = host
            self.port = port

        def connect(self):
            return httplib.HTTPConnection(self.host, self.port) # No close()

        def get(self, uri):
            c = self.connect()
            headers = {"Accept": "application/json"}
            c.request("GET", uri, None, headers)
            return c.getresponse()

        def post(self, uri, body):
            c = self.connect()
            headers = {"Content-type": "application/json"}
            c.request('POST', uri, body, headers)
            return c.getresponse()

        def put(self, uri, body):
            c = self.connect()
            if len(body) > 0:
                headers = {"Content-type": "application/json"}
                c.request("PUT", uri, body, headers)
            else:
                c.request("PUT", uri, body)
            return c.getresponse()

        def delete(self, uri):
            c = self.connect()
            c.request("DELETE", uri)
            return c.getresponse()

### 获取 access_token

{:.prettyprint}
    def test():
        json = """
        {
          "client_id": "***",
          "client_secret": "***",
          "grant_type": "password",
          "email": "***",
          "password": "***"
        }
        """
        server = TrackMasterSDK('open.admaster.com.cn')
        response = server.post("/oauth/access_token", json)

    if __name__ == "__main__":
        test()

### 获取当前用户

{:.prettyprint}
    server = TrackMasterSDK("track.admasterapi.com")
    response = server.get("/user?access_token=***")

### 获取当前用户网络

{:.prettyprint}
    server = TrackMasterSDK("track.admasterapi.com")
    response = server.get("/user/networks?access_token=***")


