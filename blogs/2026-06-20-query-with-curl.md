---
title: "QUERY with curl"
url: "https://daniel.haxx.se/blog/2026/06/21/query-with-curl/"
date: "2026-06-20"
author: "Daniel Stenberg"
feed_url: "https://daniel.haxx.se/blog/feed/"
---
This post introduces RFC 10008's new HTTP QUERY method, which functions like GET but allows request bodies and remains idempotent. It explains how to issue QUERY requests using curl's --request option and recommends the newer --follow redirect option over the legacy -L flag.
