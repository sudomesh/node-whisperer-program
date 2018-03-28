## Activity: Paper ICMP handoff
Use a piece of paper (e.g. a notecard) to represent an ICMP packet with destination address `8.8.8.8`. You could actually sketch out the whole packet, or you could just write `ICMP 8.8.8.8` and let people fill in the details in conversation.

Assign roles to participants: client (a laptop,) home node, another home node, exit node, gateway, destination, etc.

At each hop:
- How does the ICMP packet get routed?
- What decisions are made by the device?
- What information is used to make those decisions?

Ideally, someone goes down the network stack:
- Explain what ICMP is
- IP
    * Check routes
    * Get route to device or to gateway
- Optional: Explain ARP/link layer. Check ARP table to determine MAC and interface to be used, etc.

## How do we answer the above questions with a computer?
Use `ping` to "do it," and use `traceroute` to "see" the hops.

How does traceroute work? Does the output include entires consisting only of asterisks/stars? What do those mean?

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

## Getting the status of the network 
### How do we get the data on [peoplesopen.net/monitor](https://peoplesopen.net/monitor)?
Look at [`monitor.sh`](https://github.com/sudomesh/monitor/blob/master/monitor.sh) in the Sudomesh [monitor repo](https://github.com/sudomesh/monitor).

- How does this script determine the number of routes?
- How does it determine the number of gateways?

### Where does this script run?
An exit node!

### If we run it on a different node, why do we see different numbers?
TODO

## Babel
### What do we mean when we say that two or more nodes are "meshing" with each other?
If a device has an IPv4 address within the mesh subnet, then it can "mesh" with other devices by managing its routing table via Babel.

### How can we watch Babel babble?
Just run `tcpdump -n -i mesh5` on the node!

### Group activity: How does Babel / Bellman-Ford work?
Each participant acts as a node.
Define links between some participants to get a network topology.
Everyone starts with an empty routing table.
...what happens? How are the tables populated?

What happens if we make a change, like breaking a link or adding a link?

## Tunneldigger
(Lots of room for improvement here)

Suppose we have two networks, `A = {Cow, Chicken, Goat}` and `B = {Manatee, Platypus}`,
in which:
- all of the nodes in A can mesh with one another,
- all of the nodes in B can mesh with one another, *but* ...
- nodes in A cannot reach nodes in B, and vice versa.

Let's refer to A and B as distinct *submeshes*.

We use Tunneldigger to establish *exit nodes*, which solve two problems:
- connecting submeshes to the open internet
- connecting two more disparate submeshes *over* the open internet.

### So, what's an exit node?
An exit node is just a mesh node that runs a Tunneldigger *broker*, which creates tunnels to other nodes to *link parts of the mesh together* and *route traffic between the mesh and the open internet*.

Of course, as a regular old node, it's also capable of meshing directly between other nodes without Tunneldigger.

### Summary
While exit nodes facilitate access to the larger internet, they also allow us to connect disparate parts of the mesh. This is accomplished by creating `l2tp` tunnels between nodes using tunneldigger.

For example, one could connect a home node's WAN port to the home router provided by a private ISP, at which point the home node could dig a tunnel over the open internet to an exit node. This tunnel would then allow the node to access other nodes on the mesh, and vice versa.
