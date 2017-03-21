## HTTP/2.0 intro

* **1991**: HTTP/0.9
* **1996**: HTTP/1.0
* **1999**: HTTP/1.1

Average page size+++++++
Average asset count+++

High Latency on mobile. High asset count is painful.

HTTP was designed for "simple" web pages.

#### Many HTTP hacks were created to increase speed.
* **SPDY** brought forward by google, used by facebook and twitter as well.

* **2015**: HTTP/2.0
    * Increase performance
    * Increase stability

**Old truths may not be valid anymore about performance tips**\

### HTTP/1.1
DNS Lookup -> TLS handhsake -> HTTP request -> server -> HTTP response
* This already takes a lot of time
* Sends a bunch of data in the headers.

### HTTP/2.0
* For the user it functions the same way. Almost no change in Headers, Semantics
* Protocol is established during the TLS handshake
* Big changes on the transport level
    * TLS only
    * Binary instead of textual. Smaller content
    * Mutliple requests are multiplexed over one TCP connection
        * Browsers limit concorrent TCP connections to 6-35 depending on browser. Each shard requires new TCP connections and TLS handshakes. Slowed down additionally by **TCP slow start**
    * Server Push
        * Can be used to immediatly send down CSS and JS
        * Server can decide to push data to user that was not requested
    * Header compression as well as body compression
    * Smaller requests and responses, less roundtrips
    * Domain sharding no longer necessary

#### Problems with bundling
* Often leads to overfetching. More is sent than what is actually needed
* Cache invalidation. Everytime a small thing changes, the whole cache needs to be thrown out. Less caching shared between pages.

Because of multiplexing, less concantination is needed.

[Article on new standards for bundling](https://medium.com/@asyncmax/the-right-way-to-bundle-your-assets-for-faster-sites-over-http-2-437c37efe3ff#.hruaiqowv)

[http2demo](http://www.http2demo.io)
[Akamai http2 demo](https://http2.akamai.com/demo)

### Browser Support