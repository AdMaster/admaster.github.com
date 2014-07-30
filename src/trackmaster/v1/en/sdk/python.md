---
weight: 3
layout: default
category: trackmaster
subcategory: sdk
language: en
title: Python SDK
---

# TrackMaster API Python SDK

### API Sample

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

### Get an access_token

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
        server = TrackMasterSDK('open.admasterapi.com')
        response = server.post("/oauth/access_token", json)

    if __name__ == "__main__":
        test()

### Get the user

    server = TrackMasterSDK("track.admasterapi.com")
    response = server.get("/user?access_token=***")

### Get the network of user in TrackMaster

    server = TrackMasterSDK("track.admasterapi.com")
    response = server.get("/user/networks?access_token=***")


