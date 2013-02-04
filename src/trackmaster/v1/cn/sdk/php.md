---
weight: 1
layout: default
category: trackmaster
subcategory: sdk
language: cn
title: PHP SDK
---

# TrackMaster API PHP SDK

{:.prettyprint}
    class TrackmasterClient {

        function __construct($host, $port = 80) {
            $this->host = $host;
            $this->port = $port;
        }

        function get($url) {
           return $this->send("GET", $url);
        }

        function post($url, $data = null) {
            return $this->send("POST", $url, $data);
        }

        function put($url, $data = null) {
            return $this->send("PUT", $url, $data);
        }

        function delete($url) {
            return $this->send("DELETE", $url);
        }

        function send($method, $url, $post_data = NULL) {
            $s = fsockopen($this->host, $this->port, $errno, $errstr);
            if(!$s) {
                throw new Exception("$errno: $errstr");
            }

            $request = "$method $url HTTP/1.0\r\nHost: $this->host\r\n";
            $request .= "User-Agent: TrackMaster-Client-PHP\r\n";

            if ($post_data) {
                $request .= "Content-Length: ".strlen($post_data)."\r\n\r\n";
                $request .= "$post_data\r\n";
            } else {
                $request .= "\r\n";
            }

            fwrite($s, $request);
            $response = "";

            while(!feof($s)) {
                $response .= fgets($s);
            }

            list($this->headers, $this->body) = explode("\r\n\r\n", $response);
            return $this->body;
        }
    }

### 获取access_token

{:.prettyprint}
    $json = json_encode(array(
      "client_id" => "***",
      "client_secret" => "***",
      "grant_type" => "password",
      "email" => "***",
      "password" => "***"
    ));

    $client = new TrackmasterClient("open.admaster.com.cn");
    $response = $client->post("/oauth/access_token", $json);

### 获取当前用户

{:.prettyprint}
    $client = new TrackmasterClient("track.admasterapi.com");
    $response = $client->get("/user?access_token=***");

### 获取当前用户网络

{:.prettyprint}
    $response = $client->get("/user/networks?access_token=***");


