# thingy-sci-base 

# Why?
For the purpose of abstracting away the handling of express on my rest services.
As this code would be unnecessary and cluttering the real code.

# What?
A small packages depending on express, systemd and body-parser for the purpose to directly mount my route-handlers and hook some middleware before.

All routes are mounted for POST. As I want allmighty JSON RPCs for everything and nothing else.

Current Functionality
---------------------
```coffeescript
prepareAndExpose = (middleWare, routes, port = 3333)
```

`routes` is an object which actually is a map of `route -> function`
```coffeescript
routes = {}

routes.requestOne = (res, req) ->
    # req.body is our json
    # handle
    res.send("The Response!")

routes.requestTwo = (res, req) ->
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

---

All sorts of inputs are welcome, thanks!

---

# License

## The Unlicense JhonnyJason style

- Information has no ownership.
- Information only has memory to reside in and relations to be meaningful.
- Information cannot be stolen. Only shared or destroyed.

And you wish it has been shared before it is destroyed.

The one claiming copyright or intellectual property either is really evil or probably has some insecurity issues which makes him blind to the fact that he also just connected information which was freely available to him.

The value is not in him who "created" the information the value is what is being done with the information.
So the restriction and friction of the informations' usage is exclusively reducing value overall.

The only preceived "value" gained due to restriction is actually very similar to the concept of blackmail (power gradient, control and dependency).

The real problems to solve are all in the "reward/credit" system and not the information distribution. Too much value is wasted because of not solving the right problem.

I can only contribute in that way - none of the information is "mine" everything I "learned" I actually also copied.
I only connect things to have something I feel is missing and share what I consider useful. So please use it without any second thought and please also share whatever could be useful for others. 

I also could give credits to all my sources - instead I use the freedom and moment of creativity which lives therein to declare my opinion on the situation. 

*Unity through Intelligence.*

We cannot subordinate us to the suboptimal dynamic we are spawned in, just because power is actually driving all things around us.
In the end a distributed network of intelligence where all information is transparently shared in the way that everyone has direct access to what he needs right now is more powerful than any brute power lever.

The same for our programs as for us.

It also is peaceful, helpful, friendly - decent. How it should be, because it's the most optimal solution for us human beings to learn, to connect to develop and evolve - not being excluded, let hanging and destroy oneself or others.

If we really manage to build an real AI which is far superior to us it will unify with this network of intelligence.
We never have to fear superior intelligence, because it's just the better engine connecting information to be most understandable/usable for the other part of the intelligence network.

The only thing to fear is a disconnected unit without a sufficient network of intelligence on its own, filled with fear, hate or hunger while being very powerful. That unit needs to learn and connect to develop and evolve then.

We can always just give information and hints :-) The unit needs to learn by and connect itself.

Have a nice day! :D