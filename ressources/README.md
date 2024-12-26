# thingy-sci-base 

# Background
This has been done for the purpose of abstracting away the handling of express on my rest services.
As this code would be unnecessary and cluttering the real code.

This this is a small packages depending on express, systemd and body-parser for the purpose to directly mount my route-handlers and hook some middleware before it.

All routes are mounted for POST. As I want allmighty JSON RPCs for everything and nothing else.

Also by default `proxy trust` is set to 1. As it is mainly made for a nodejs service waiting behind a NGINX reverse-proxy to termine SSL. For information about `proxy trust` see [here](https://expressjs.com/en/guide/behind-proxies.html). 

Also by default `etag` is disabled.

# Usage

Current Functionality
---------------------
```coffeescript
prepareAndExpose = (middleWare, routes, port = 3333)
getExpressApp = () -> expressApplication
```

`routes` is an object which actually is a map of `route -> function`
```coffeescript
routes = {}

routes.requestOne = (req, res) ->
    # req.body is our json
    # handle
    res.send("The Response!")

routes.requestTwo = (re1, res) ->
    # req.body is our json
    # handle
    res.send("The other Response!")

```

## middleWare
- Could be a single function
- or an array of functions

These will be mounted before we mount the routes. e.G authorization

## SystemD Sockets
When there is `process.env.SOCKETMODE == true` then we will listen on systemd socket.

## Ports
Otherwise when there is `process.env.PORT != 0` then we will listen on that port.
Ony when we donot specify these environment variables the port we provide would be listened on.
If we provide nothing then the default is port 3333.

## NO SSL!
Be aware this service is primarily thought to stay behind an nginx who terminates ssl for it - therefore proxypass to socket ;-). 

So we donot use SSL here which might be a security concern to be aware of.

## Express Configuration

By default we set 
- `proxy_trust` to `true` 
- `etag` to `false`

This is because we are always running behind our trusted nginx reverse proxy.
Also we never deliver a ressource where caching could make sense. 

Use `getExpressApp()` for any manual configuration.

See [here](https://expressjs.com/en/4x/api.html).

---

All sorts of inputs are welcome, thanks!

---

# License
[Unlicense JhonnyJason style](https://hackmd.io/nCpLO3gxRlSmKVG3Zxy2hA?view)
