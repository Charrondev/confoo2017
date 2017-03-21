## Building Interactivity with WebSockets
*by Wim Godden @wimgtr*

Websockets offer real time connectivity. Key to keep users on the platform.

### History

* Original implementation: refresh the page at a set interval

    *delayed, not efficient, strain on server, visually jarring*

* First real time implementation: AJAX polling

    *polling in javascript for updated changes then change page in js. Still uses a lot of bandwith. Lots of http overhead. High server load.*

* Long polling

    *Facebook still uses in their chat. Server doesn't respond if there are no updates. Will keep http request until changes happen. Near realtime, less bandwith use, server load is not as high, but the server must be able to handle a lot of long constantly open connections.*

* SSE (Sent server Events)

    *Works slightly differently than long polling. One way only. Not supported in IE or Edge*

* **WebSockets**

    *Clients makes a connection to server over http/https, then upgrades the connection from http to WebSockets. Bidirectional full duplex in real time.*

#### Initiation - Handshake

```
GET /link HTTP/1.1
Host: yourhost.com
Upgade: websocket
Connection: upgrade
Origin: http://yourhost.com
Sec-Websocket-Key: asdfaagsf32rsdfad=
Sec-Websocket-Protocol: chat/etc/custom
Sec-Websocket-Version: 13
```

*reply*

```
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: upgrade
Sec-Websocket-Accept: awefawefawrgsdf42r2fsd=
Sec-Websocket-Protocol: chat/etc/custom whatever you want here
```

#### Protocols

* Must be supported by client and server
* Several exist
    * WAMP (provides PubStub)
    * chat
    * superchat
    * custom ones

#### Events

#### Support
All HTML5 compliant browsers should have support

* IE 10+
* Chrome 16+
* Safari 5+
* Firefox 11+
* Opera 12+
* Adnroid Browser 4.4+
* User socket.io to fallback to long polling

#### Advantages

* Full duplex messaging
* 100% async
* http overhead only on handshake
* low latency
* low bandwith
* messages can be fragmented
    * Partial sends (when not complete)
    * Sent in-between other messages

#### Disadvantages

* No caching unlike HTTP
* Some applications changes required
* No message acknowledgement built-in
* Ping-pong (present in RFC not in most browsers) to keep-alive connection
    * Write your own
    * Use socket.io

#### Client code

```
const ws = new WebSocket('ws://www.websockets.org')

ws.onopen = (e) => {
    console.log('Connection open...)
}

ws.onmessage = (e) => {
    copnsole.log(e.data)
}

ws.onclose = (e) => {}

ws.send("Hello websocket")
ws.close()
```

#### Sending information

Any type of data including binary data is supported as long as both sides can parse it.

#### PHP Library: Ratchet

#### Security

* Always use TLS (`wss://` instead of `ws://`)
* Verify the `Origin` header
* Pass along a random token to the handshake request, session cookie, any authentication

#### Tips and tricks

* If you proxy WebSocket through Nginx
    * Set `proxy_read_timeout` and `proxy_send_timeout` so you're websocket connection is kept alive.
* Check [websocket.org](http://websocket.org)
* Use Chrome dev console
* Use Thor or Websocket-bench for benchmarking
* Use Socket.io or SockJS for backwards compatibility