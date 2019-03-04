---
layout: post
title:      "Sinatra With Sessions And Authentication"
date:       2019-03-04 20:31:21 +0000
permalink:  sinatra_with_sessions_and_authentication
---


## What  Are Sessions And Why Do I Need Them?
The internet or rather the HTTP protocol that we use and know today was invented by a guy named Tim Berners-Lee. 
He built the internet to be stateless, meaning that every time you request a page from a webserver the webserver does not know or care who you are. Same so every time you submit a webpage to a webserver it has no special meaning to the web server.

The reason why HTTP was designed to be stateless and not remember who is who was to optimize and reduce server load. 
Stateful protocols require that the server keep an open connection to the client - your browser, at all times. Having many open connections can quickly add up costing you resources and eventually money.

So how as web developers do we authenticate and know who is requesting a particular page and do they have the right to view that requested page?

Meet the session:

## The session
A session is a way for your server to store data about a particular user so it can remember who logged in.
The way it accomplishes that is by creating a session identifier or key and storing it in your web browser.
Data is stored in web browser by the means of a cookie.

The process of an authenticated session:
1. A user logs on to a website
2. The server will try to authenticate the user and if successesful create a session
3. The session will generate a unique key
4. The server will pass along that key to get stored in your browser
5. The key will live in a cookie saved to your browser
6. You request a page, the cookie gets passed along to the webserver
7. The webserver reads the cookie and matches it with your session

## The Cookie
Cookies are small files that cannot be executed or execute. They are small snippets of data which allows the server to store info about the user.

That's that,
Heshie

