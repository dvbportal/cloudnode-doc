HTTP Caching
============

All hosted NodeJS apps leverage a HTTP cache on Cloudnode. We are using
\ `Varnish <http://www.varnish-cache.org/>`_\  as a HTTP accelerator.
Varnish uses numerous techniques to improve the performance. It even has
compiled configuration libraries, in-memory logging, and works hand in
hand with the OS for memory management.

Cache Invalidation
~~~~~~~~~~~~~~~~~~

The biggest challenge when using caching is the control of the cache TTL
and cache invalidation. Varnish only delivers a cached page, when it is
absolutely safe to do so. The URL and all parameters have to match for a
cache hit. So a Node app can control caching in different ways. Per
default no caching takes place, but you should decide which pages or
parts of your app could benefit from caching. Your application's
response time will improve dramatically when you take the advantage of
caching.

Cache TTL Control
~~~~~~~~~~~~~~~~~

Every application that is hosted on Cloudnode, even when running on a
custom domain, leverages the caching layer. The time to live, or TTL,
can easily be controlled using Node's response.setCacheable() call. By
default, pages are not cached. When set to true, pages are cached for a
long time, a perfect choice for pictures and other static content. When
set to undefined, the cache headers need to be supplied by the
application. This option allows custom control of the cache TTL times.
