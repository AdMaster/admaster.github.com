---
weight: 3
layout: default
category: openmaster
language: en
title: OAuth
version: v1
---

# OAuth

* TOC
{:toc}

OAuth2 is a protocol that lets external apps request authorization to private details in a user’s OpenMaster account without getting their password. This is preferred over Basic Authentication because tokens can be limited to specific types of data, and can be revoked by users at any time.

All developers need to register their application before getting started. A registered OAuth application is assigned a unique Client ID and Client Secret. The Client Secret should not be shared. Please




## Web Application Flow

This is a description of the OAuth flow from 3rd party web sites.

### 1. Redirect users to request OpenMaster access

    GET http://open.admaster.com.cn/oauth/authorize

**Parameters**

`client_id`
: _Required_ **string** - The client ID you received from OpenMaster when you [registered](http://open.admaster.com.cn/app/new).

`response_type`
: _Required_ **Enum** - Type，`code`, `token`

`redirect_uri`
: _Optional_ **string** - URL in your app where users will be sent after authorization.

`scope`
: _Optional_ **string** - Comma separated list of scopes.

### 2. OpenMaster redirects back to your site

If the user accepts your request, OpenMaster redirects back to your site with a temporary code in a code parameter as well as the state you provided in the previous step in a state parameter. 

Get access token：

    POST http://open.admaster.com.cn/oauth/access_token

**Parameters**

`client_id`
: _Required_ **string** - The client ID you received from OpenMaster when you [registered](http://open.admaster.com.cn/app/new).

`client_secret`
: _Required_ **string** - The client secret you received from OpenMaster when you [registered](http://open.admaster.com.cn/app/new).

`grant_type`
: _Required_ **enum** - `password` `refresh_token` `authorization_code`

`redirect_uri`
: _Optional_ **string**

`code`
: _Optional_ **string** - The code you received as a response to Step 1. Pass `code` as a parameter when the type of `grant_type` is `authorization_code`.


`email`
: _Optional_ **string** - Email  
Pass `email` as a parameter when the type of `grant_type` is `password`.

`password`
: _Optional_ **string** - Password  
Pass `email` as a parameter when the type of `grant_type` is `password`.

`refresh_token`
: _Optional_ **string** - Refresh Token  
Pass `refresh_token` as a parameter when the type of `grant_type` is `refresh_token`.

**响应**

{:.prettyprint}
    {
      "access_token": "7a68b4d65ddd6a6191ef0cbf9cadb06528d92d67",
      "expires_in": "1800000",
      "refresh_token": "23a89c9944afc0525a25d15d180c6bce03efa331"
    }


### 3. Use the access token to access the API

The access token allows you to make requests to the API on a behalf of a user.

    GET http://open.admaster.com.cn/user?access_token=...

**Response**

{:.prettyprint}
    {
  	"email": "hello@admaster.com.cn",
  	"username": "hello",
  	"uuid": "higklmn",
  	"client_id": "abcdefg"
    }


## Non-Web Application Flow

Use basic authentication to create an OAuth2 token using the interface below. With this technique, a username and password need not be stored permanently, and the user can revoke access at any time.

## Redirect URLs

The `redirect_uri` parameter is optional. If left out, OpenMaster will redirect users to the callback URL configured in the OAuth Application settings. If provided, the redirect URL must match the callback URL’s host.

    CALLBACK: http://foo.com

    GOOD: http://foo.com
    GOOD: http://foo.com/bar
    BAD:  http://foo.com:8080
    BAD:  http://oauth.foo.com:8080
    BAD:  http://bar.com

## Scopes

Scopes let you specify exactly what type of access you need. This will be displayed to the user on the authorize form.

Check headers to see what OAuth scopes you have, and what the API action accept.

    $ curl -H "Authorization: bearer TOKEN" http://open.admaster.com.cn/user/1 -I
    HTTP/1.1 200 OK
    X-OAuth-Scopes: brand, user
    X-Accepted-OAuth-Scopes: user

`X-OAuth-Scopes` lists the scopes your token has authorized.
`X-Accepted-OAuth-Scopes` lists the scopes that the action checks for.

(no scope)  
	public read-only access (includes public user profile info, public repo info, and gists).

user   
	Read/write access to profile info only.

NOTE: Your application can request the scopes in the initial redirection. You can specify multiple scopes by separating them by a comma.

    http://open.admaster.com.cn/oauth/authorize?client_id=...&scope=user,brand


## More Information

It can be a little tricky to get started with OAuth. Here are a few links that might be of help:

* [OAuth 2 spec](http://tools.ietf.org/html/draft-ietf-oauth-v2-07)
* [Facebook API](http://developers.facebook.com/docs/authentication/)
* [Ruby OAuth2 lib](http://github.com/intridea/oauth2)
* [simple ruby/sinatra example](http://gist.github.com/9fd1a6199da0465ec87c)
* [simple python example](http://gist.github.com/e3fbd47fbb7ee3c626bb) using [python-oauth2](http://github.com/dgouldin/python-oauth2)
* [Ruby OmniAuth example](http://github.com/intridea/omniauth)

