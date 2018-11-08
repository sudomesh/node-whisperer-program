## Investigating the routing table
### How does `traceroute` know where to send packets?
It references the routing table, just like everything else!

## How can we see it on a home node?
Suppose our home node, Manatee, has IP address `100.65.91.65`.
We can connect to Manatee's private wifi and run `ssh root@100.65.91.65`.

From the node, we can run `ip route show table public`.

## What are we seeing here?
Suppose our output looks something like this:
```
default via 100.65.7.1 dev mesh5 proto babel onlink
(...)
100.65.8.0/26 via 100.65.7.1 dev mesh5 proto babel onlink
100.65.8.3 via 100.65.7.1 dev mesh5 proto babel onlink
100.65.8.64/26 via 100.65.7.1 dev mesh5 proto babel onlink
(...)
```

- What is the `default` entry?
- What role is `100.65.7.1` playing?
- What does the `/26` in `100.65.8.0/26` mean? How is that entry different from the one for `100.65.8.3`?
- Which gateway is used to reach `100.65.8.80`? Which interface is used to route packets to this gateway?

## Exercise: Getting the status of the network 
### How do we get the data on [peoplesopen.net/monitor](https://peoplesopen.net/monitor)?
Look at [`monitor.sh`](https://github.com/sudomesh/monitor/blob/master/monitor.sh) in the Sudomesh [monitor repo](https://github.com/sudomesh/monitor).

- How does this script determine the number of routes?
- How does it determine the number of gateways?

### Where does this script run?
An exit node!

### If we run it on a different node, why do we see different numbers?
TODO
