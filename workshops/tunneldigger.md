## Tunneldigger
(Lots of room for improvement here)

### Setting
Suppose we have two networks, `A = {Cow, Chicken, Goat}` and `B = {Manatee, Platypus}`,
in which:
- all of the nodes in `A` can mesh with one another via wireless connections,
- all of the nodes in `B` can mesh with one another via wireless connections, *but* ...
- nodes in `A` cannot reach nodes in `B`, and vice versa.

Let's refer to `A` and `B` as distinct "submeshes".
They could be in different neighborhoods or even different continents.
They can be anywhere!

We want to solve two problems:
- connecting "submeshes" to the Internet
- connecting two more disparate submeshes *over* the Internet.

We solve both issues by maintaining one or more *exit nodes*.
An exit node is just another mesh node that runs a program called Tunneldigger.
Before we talk about exit nodes, let's talk about a possible solution
to the first problem.

### Connecting a node to the Internet
If a mesh node happens to have a WAN (Wide Area Network) connection,
e.g. from an ISP,
then it *could* just add routing rule to expose its WAN connection to the mesh.

This could be cool, but it doesn't work for connecting disparate submeshes.
Even worse, it creates a new problem!

With this setup, all the mesh traffic that exits from your node appears to be *your* traffic.
So, if your ISP, your government, or your dog is watching your traffic,
then it looks like *you* did all of *my* web browsing!
Trust me, your dog would be jealous of all the dog GIFs I watch.

Instead, nodes with a WAN connection can "dig a tunnel" to an exit node.
Now, all the traffic going through your node to the Internet appears to come from
the exit node's IP address, not yours.
Even better, your mesh can now see other meshes that dig tunnels to the same exit node!
Let's talk about what the exit node actually is, then we'll dig into the nature of the tunnels.

### So, what's an exit node?
An exit node is just another node on the mesh!
There are only a few distinctions between exit nodes and normal nodes.
- An exit node has a public IP address on the capital-I Internet in addition to its mesh address.
- An exit node is probably a fancy server, not a home router.
- An exit node runs a special application called a Tunneldigger *broker*.

The broker manages tunnels from other nodes to *link parts of the mesh together* and *route traffic between the mesh and the Internet*.

Of course, as a regular old node,
it's also capable of meshing directly between other nodes without Tunneldigger
if it has a direct connection to the mesh.

### What's a tunnel?
TODO (something something l2tp something UDP)
- What's a tunnel
- Creating tunnel interfaces
- Bridging tunnels, routing to WAN

### Back to the example
So, we could create an exit node `E` with a public IP address.
Suppose that `Cow` can reach `E` over a WAN connection provided by `Cow`'s ISP,
and `Platypus` can reach `E` over the WAN connection in her dorm room.

Then, they can each "dig tunnels" to `E`.

Since `E` is just another node, it routes traffic from `Cow` to `Platypus` and vice versa,
connecting mesh `A` with mesh `B`.

### Summary
While exit nodes facilitate access to the larger internet,
they also allow us to connect disparate parts of the mesh.
This is accomplished by creating `l2tp` tunnels between nodes using tunneldigger.

For example, one could connect a home node's WAN port to the home router provided by a private ISP,
at which point the home node could dig a tunnel over the Internet to an exit node.
This tunnel would then allow the node to access other nodes on the mesh, and vice versa.
