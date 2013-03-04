---
weight: 14
layout: default
category: openmaster
language: en
title: Protocal and Requests Instructions
---

# {{ page.title }}

This describes the resources that make up the official Admaster API. 

* TOC
{:toc}

## Schema

All API access is over HTTP. All data is sent and received as JSON.

    $ curl -i https://track.admasterapi.com

{:.prettyprint}
    HTTP/1.1 302 Found
    Server: nginx/1.0.12
    Date: Mon, 20 Feb 2012 11:15:49 GMT
    Content-Type: text/html;charset=utf-8
    Connection: keep-alive
    Status: 302 Found
    X-RateLimit-Limit: 5000
    ETag: "d41d8cd98f00b204e9800998ecf8427e"
    Location: http://developer.admaster.com.cn
    X-RateLimit-Remaining: 4999
    Content-Length: 0


Blank fields are included as `null` instead of being omitted.

All timestamps are returned in ISO 8601 format：`YYYY-MM-DDTHH:MM:SSZ`

##  Client Errors

There are three possible types of client errors on API calls that receive request bodies:

1.Sending invalid JSON will result in a `400 Bad Request` response.

    HTTP/1.1 400 Bad Request
    Content-Length: 35

{:.prettyprint}
    {"message":"Problems parsing JSON"}


2.Sending the wrong type of JSON values will result in a` 400 Bad Request` response.

    HTTP/1.1 400 Bad Request
    Content-Length: 40

{:.prettyprint}
    {"message":"Body should be a JSON Hash"}


3.Sending invalid fields will result in a `422 Unprocessable Entity` response.

    HTTP/1.1 422 Unprocessable Entity
    Content-Length: 149

{:.prettyprint}
    {
      "message": "Validation Failed",
      "errors": [
        {
          "resource": "Issue",
          "field": "title",
          "code": "missing_field",
          "value":"Resource Value"
        }
      ]
    }

All error objects have resource and field properties so that your client can tell what the problem is. There’s also an error code to let you know what is wrong with the field. These are the possible validation error codes:

* `missing` This means a resource does not exist.
* `missing_field` This means a required field on a resource has not been set.
* `invalid` This means the formatting of a field is invalid. The documentation for that resource should be able to give you more specific information.
* `already_exists` This means another resource has the same value as this field. This can happen in resources that must have some unique key (such as Label names).

If resources have custom validation errors, they will be documented with the resource.

##  HTTP Verbs

Where possible, Admaster API strives to use appropriate HTTP verbs for each action.

`HEAD` Can be issued against any resource to get just the HTTP header info.

`GET` Used for retrieving resources.

`POST` Used for creating resources, or performing custom actions (such as merging a pull request).

`PATCH` Used for updating resources with partial JSON data. For instance, an Issue resource has `title` and `body` attributes. A PATCH request may accept one or more of the attributes to update the resource. PATCH is a relatively new and uncommon HTTP verb, so resource endpoints also accept POST requests.

`PUT` Used for replacing resources or collections. For PUT requests with no `body` attribute, be sure to set the `Content-Length` header to zero.

`DELETE` Used for deleting resources.

## Authentication


OAuth2 Token (sent in a header):

    $ curl -H "Authorization: token OAUTH-TOKEN" http://track.admasterapi.com


OAuth2 Token (sent as a parameter):

    $ curl http://track.admasterapi.com/advertisers?access_token=OAUTH-TOKEN


Requests that require authentication will return 404, instead of 403, in some places. This is to prevent the accidental leakage of private repositories to unauthorized users.

## Pagination

Requests that return multiple items will be paginated to 30 items by default. You can specify further pages with the `?page` parameter. For some resources, you can also set a custom page size up to 100 with the `?per_page` parameter.

    $ curl http://track.admasterapi.com/advertisers?page=2&amp;per_page=100


The pagination info is included in the link header：

{:.prettyprint}
    Link: <http://track.admasterapi.com/advertisers?page=3&per_page=100>; rel=”next”, 
      <http://track.admasterapi.com/advertisers?page=50&per_page=100>; rel=”last”

Linebreak is included for readability.

The possible `rel` values are:

* `next` Shows the URL of the immediate next page of results.
* `last` Shows the URL of the last page of results.
* `first` Shows the URL of the first page of results.
* `prev` Shows the URL of the immediate previous page of results.


## Rate Limiting(Planning)

We limit requests to 5,000 per hour. You can check the returned HTTP headers of any API request to see your current status:

{:.prettyprint}
    $ curl -i https://track.admasterapi.com/users/whatever

    HTTP/1.1 200 OK
    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4966

Please contact us to request white listed access for your application. We prefer sites that setup OAuth applications for their users.

## Cross Origin Resource Sharing

The API supports Cross Origin Resource Sharing (CORS) for AJAX requests. you can read the CORS W3C working draft from the HTML 5 Security Guide.


Here’s a sample request sent from a browser hitting`http://some-site.com`：

    $ curl -i https://track.admasterapi.com -H "Origin: http://some-site.com" 
    HTTP/1.1 302 Found

Any domain that is registered as an OAuth Application is accepted. Here’s a sample request for a browser hitting Calendar About Nothing:

    $ curl -i https://track.admasterapi.com -H "Origin: http://calendaraboutnothing.com" 

{:.prettyprint}
    HTTP/1.1 302 Found
    Access-Control-Allow-Origin: http://calendaraboutnothing.com
    Access-Control-Expose-Headers: Link, X-RateLimit-Limit, X-RateLimit-Remaining, X-OAuth-Scopes, X-Accepted-OAuth-Scopes
    Access-Control-Allow-Credentials: true


This is what the CORS preflight request looks like：

    $ curl -i https://track.admasterapi.com -H "Origin: http://calendaraboutnothing.com" -X OPTIONS   

{:.prettyprint}
    HTTP/1.1 204 No Content
    Access-Control-Allow-Origin: http://calendaraboutnothing.com
    Access-Control-Allow-Headers: Authorization, X-Requested-With
    Access-Control-Allow-Methods: GET, POST, PATCH, PUT, DELETE
    Access-Control-Expose-Headers: Link, X-RateLimit-Limit, X-RateLimit-Remaining, X-OAuth-Scopes, X-Accepted-OAuth-Scopes
    Access-Control-Max-Age: 86400
    Access-Control-Allow-Credentials: true


## JSON-P Callbacks(Planning)

You can send a `?callback`parameter to any GET call to have the results wrapped in a JSON function.The response includes the same data output as the regular API, plus the relevant HTTP Header information.

    $ curl https://track.admasterapi.com/advertisers?callback=foo

{:.prettyprint}
    foo({
      "meta": {
        "status": 200,
        "X-RateLimit-Limit": "5000",
        "X-RateLimit-Remaining": "4966",
        "Link": [ // pagination headers and other links
          ["https://track.admasterapi.com/advertisers?page=2", {"rel": "next"}]
        ]
      },
      "data": {
        // the data
      }
    })


You can write a javascript handler to process the callback like this:

    $ curl https://track.admasterapi.com/advertisers?callback=foo

{:.prettyprint}
    foo({
      "meta": {
        "status": 200,
        "X-RateLimit-Limit": "5000",
        "X-RateLimit-Remaining": "4966",
        "Link": [ // pagination headers and other links
          ["https://track.admasterapi.com/advertisers?page=2", {"rel": "next"}]
        ]
      },
      "data": {
        // the data
      }
    })



All of the headers are the same String value as the HTTP Headers with one notable exception: Link. Link headers are pre-parsed for you and come through as an array of `[url, options]` tuples.

A link that looks like this:

{:.prettyprint}
    Link: <url1>; rel=”next”, <url2>; rel=”foo”; bar=”baz”


… will look like this in the Callback output:

{:.prettyprint}
    {
      "Link": [
        [
          "url1",
          {
            "rel": "next"
          }
        ],
        [
          "url2",
          {
            "rel": "foo",
            "bar": "baz"
          }
        ]
      ]
    }
