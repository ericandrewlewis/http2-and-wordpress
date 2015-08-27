# HTTPS, HTTP/2 and WordPress

[HTTP/2](https://http2.github.io/) is the next version of the HTTP protocol with
a focus on performance.

[Compare HTTP/1.1 and 2 with varying latency](https://http2.golang.org/gophertiles?latency=0).

All browser implementations require encryption, which means HTTPS is a requirement for HTTP/2.

## HTTP/2 support

The latest versions of most major browsers [support HTTP/2](http://caniuse.com/#feat=http2).

Both NGINX and Apache have HTTP/2 support in an alpha stage.

NGINX has a patch for HTTP/2 (see [alpha release notes](https://www.nginx.com/blog/early-alpha-patch-http2/)).
They have not committed to supporting Server Push.

An [Apache module](https://github.com/icing/mod_h2) is in alpha for HTTP/2 support.

[nghttp2](https://nghttp2.org/) includes an HTTP/2 proxy ([nghttpx](https://nghttp2.org/documentation/nghttpx-howto.html)).
This is a way to support the protocol without running alpha versions of web server software.

The HTTP/2 organization lists [a horde of other implementations](https://github.com/http2/http2-spec/wiki/Implementations).

## HTTPS and HTTP/2 setup guides

[HTTPS Setup Guide](/https-setup-guide.md)

[HTTP/2 Setup Guide](/http2-setup-guide.md)

## Other notes

Placing WordPress behind an HTTPS proxy that requests WordPress over HTTP causes
WordPress to think it's running over HTTP (i.e. [`is_ssl()`](https://github.com/WordPress/WordPress/blob/master/wp-includes/functions.php#L3748) will return false).
Modifying `$_SERVER` variables in `wp-config.php` is the suggested configuration.
See trac tickets #9235, #19654, #31288.