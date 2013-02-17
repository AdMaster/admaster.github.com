---
weight: 1
layout: default
category: trackmaster
subcategory: sdk
language: en
title: C# SDK
---

# TrackMaster API C`#` SDK

### API Sample

{:.prettyprint}
    using System;
    using System.IO;
    using System.Net;
    using System.Text;
    using System.Web;

    namespace Admaster{
        public class TrackmasterClient {
            private HttpWebRequest request;

            private string uri;

            public TrackmasterClient(string host)
            {
                this.uri = "http://" + host;
            }

            public HttpWebResponse Request(string method, string path, string data)
            {
                request = (HttpWebRequest)WebRequest.Create(this.uri + path);
                request.Headers.Clear(); //important
                request.Headers.Add("Accept-Charset", "utf-8");
                request.Accept = "application/json";
                request.Referer= this.uri;
                request.ContentType = "application/json";
                request.Timeout = 10000;
                request.Method = method;
                return this.GetResponse(request, data);
            }

            public HttpWebResponse Get(string path) {
                return Request("GET", path, null);
            }

            public HttpWebResponse Post(string url, string data) {
                return Request("POST", url, data);
            }

            public HttpWebResponse Put(string path, string data) {
                return Request("PUT", path, data);
            }

            public HttpWebResponse Delete(string path) {
                return Request("DELETE", path, null);
            }

            public HttpWebResponse GetResponse(HttpWebRequest request, String data)
            {
                if (request.Method == "POST")
                {
                    ASCIIEncoding encoding = new ASCIIEncoding();
                    byte[] b = encoding.GetBytes(data);
                    request.ContentLength = b.Length;
                    using (Stream stream = request.GetRequestStream())
                    {
                        stream.Write(b, 0, b.Length);
                    }
                }
                try
                {
                    HttpWebResponse res = (HttpWebResponse)request.GetResponse();
                    return res;
                } catch (WebException webEx) {
                    throw webEx;
                }
            }

            public String ResultData(HttpWebResponse response)
            {
                string result = string.Empty;
            try
            {
                using (StreamReader reader = new StreamReader(response.GetResponseStream(), Encoding.GetEncoding("utf-8")))
                {
                    result = reader.ReadToEnd();
                }
            }
            catch (Exception ex)
            {
                result ="发生异常\n\r" + ex.Message;
            }
            return result;
            }
        }
    }


### Get an access_token

{:.prettyprint}
    String client_id = "\"Your client_id\"";
    String client_secret = "\"Your client_secret\"";
    String grant_type = "\"password\"";
    String password = "\"Your password\"";
    String email = "\"Your email\"";
    String json = "{\"client_id\":" + client_id
        + ",\"client_secret\":" + client_secret
        + ",\"grant_type\":" + grant_type
        + ",\"email\":" +email
        + ",\"password\":" +password+"}";
    TrackmasterClient client = new TrackmasterClient("testopen.admasterapi.com");
    HttpWebResponse response = client.Post("/oauth/access_token", json);
    String data = client.ResultData(response);

### Get the user

{:.prettyprint}
    TrackmasterClient client = new TrackmasterClient("track.admasterapi.com");
    HttpWebResponse response = client.Get("/user?access_token=***");
    String data = client.ResultData(response);

### Get the network of user in TrackMaster

{:.prettyprint}
    TrackmasterClient client = new TrackmasterClient("track.admasterapi.com");
    HttpWebResponse response = client.Get("/user/networks?access_token=***");
    String data = client.ResultData(response);
