# Relative Path Overwrite demo

RPO ("***Relative Path Overwrite***") is an elaborate attack technique that takes advantage of relative links to overwrite its target.

As described in the various RFCs ([RFC-1738 - Uniform Resource Locators (URL)](https://tools.ietf.org/html/rfc1738), [RFC-1808 - Relative Uniform Resource Locators (URL)](https://tools.ietf.org/html/rfc1808), [RFC-3986 - Uniform Resource Identifier (URI): Generic Syntax](https://tools.ietf.org/html/rfc3986)):

 - A URL is a specific scheme of *Uniform Resource Identifier* (URI) designed to create references to web resources;
 - Each URI conforms to a generic syntax (defined as `scheme://user:password@host:port/path?query#fragment` in RFC 3986) which consists of a hierarchical sequence of components and subcomponents referred to as the scheme (e.g., `scheme://`), authority (e.g., `user:password@host:port`), path (e.g., `/path`), query (e.g., `?query`) and fragment (e.g., #fragment);
 - URI components are delimited by characters in a "reserved" set. Thus, component-wide data characters belong to this reserved set must be percent-encoded to prevent conflicts with a reserved character's purpose as a delimiter. In this way, a URI that differ in the replacement of a reserved character with its corresponding **percent-encoded octet shouldn't be equivalent** and **should change how the URI is interpreted by the application** (backend and frontend).

An absolute URL is basically the "full URL" for a destination address (e.g., `https://www.bmoine.fr/assets/js/core.js?v=deadbeef#sha384-bOt9mrX4bzGOgv1vRvIwO4xe0VxLbHznZCMN9YnlBhsfW2149mKXNdhNQXXwYTno`) including the scheme (e.g., `https:`), the authority (e.g., `www.bmoine.fr`), the path (e.g., `/assets/js/core.js`) and enventually, the query (e.g., `?v=deadbeef`) and fragment part (e.g., `#sha384-bOt9mrX4bzGOgv1vRvIwO4xe0VxLbHznZCMN9YnlBhsfW2149mKXNdhNQXXwYTno`).

Whereas a relative URL doesn’t specify the scheme nor the authority and instead refers to a resource by describing the difference within a hierarchical name space between the existing location and the target URL (e.g., `assets/js/core.js?v=deadbeef#sha384-bOt9mrX4bzGOgv1vRvIwO4xe0VxLbHznZCMN9YnlBhsfW2149mKXNdhNQXXwYTno` from location `https://www.bmoine.fr/`).

Knowing this, and while admitting that the webpage is using relative links to import its resources, there is sometimes the ability to play with the current location without changing the content that's delivered from the HTTP service, for exemple, using a dot-dot-slash attack (Directoy traversal). In fact I've found a frontend variant using the `path` component of URL that enables a Relative Path Overwrite attack, whereas traditional dot-dot-slash exploits `query` component of the URL to perform a backend attack.

Further Reading:

 - [RPO](http://www.thespanner.co.uk/2014/03/21/rpo/)
 - [Relative Path Overwrite](http://support.detectify.com/customer/portal/articles/2088351-relative-path-overwrite)
 - [Path-Relative Stylesheet import (PRSSI)](http://blog.portswigger.net/2015/02/prssi.html)
 - [Directory traversal attack](https://en.wikipedia.org/wiki/Directory_traversal_attack)
 - [Subresource Integrity (SRI)](https://frederik-braun.com/using-subresource-integrity.html)
 - [A CDN that can not XSS you: Using Subresource Integrity](https://frederik-braun.com/using-subresource-integrity.html)
 - [W3C - Subresource Integrity](https://w3c.github.io/webappsec-subresource-integrity/)

## Video demo

[![Relative Path Overwrite Cross-Site Scripting demo](https://img.youtube.com/vi/gnQtOtku5_A/maxresdefault.jpg)](https://www.youtube.com/watch?v=gnQtOtku5_A "Relative Path Overwrite Cross-Site Scripting demo")

Please let me know if you need more information!
