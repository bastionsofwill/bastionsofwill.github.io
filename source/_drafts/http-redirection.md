---
title: http-redirection
tags:
---
## Redirections in HTTP
URL redirection(=URL forwarding) is a technique to give more than one URL address to a page, a form, or a whole Web site/application. HTTP has a special kind of response, called a HTTP redirect, for this operation.

There are two categories:
- Temporary redirects during site maintenance or downtime
- Permanent redirects to preserve existing links/bookmarks after changing the site's URLs, progress pages when uploading a file, etc.

## Principle
In HTTP, redirection is triggered by a server sending a special redirect response to a request. Redirect responses have status codes that start with 3, and a Location header holding the URL to redirect to. 
When browsers receive a redirect, they immediately load the new URL provided in the Location header.

## Permanent redirections
These redirections are meant to last forever. They imply that the original URL should no longer be used, and replaced with the new one. Search engine robots, RSS readers, and other crawlers will update the original URL for the resource.

|   Code   |     Text     |  Method handling |  Typical use case |
|----------|-------------|-------------|------|
| 301 | Moved Permanetly | GET methods unchanged. Others may or may not be changed to GET. | Reorganization of a Web site.
| 308 | Permanent Redirect | Method and body not changed. | Reorganization of a Web site, with non-Get links/operations |

## Temporary redirections


## 301 and 302 redirect

https://developer.mozilla.org/en-US/docs/Web/HTTP/Redirections