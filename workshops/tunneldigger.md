## Tunneldigger
(Lots of room for improvement here)

Suppose we have two networks, `A = {Cow, Chicken, Goat}` and `B = {Manatee, Platypus}`,
in which:
- all of the nodes in A can mesh with one another via wireless connections,
- all of the nodes in B can mesh with one another via wireless connections, *but* ...
- nodes in A cannot reach nodes in B, and vice versa.

Let's refer to A and B as distinct *submeshes*.
They could be in different neighborhoods or even different continents. It's all good!

We use Tunneldigger to establish *exit nodes*, which solve two problems:
- connecting submeshes to the open internet
- connecting two more disparate submeshes *over* the open internet.

In particular, we could create an exit node E with a public IP address.
Suppose that Cow can reach E over a WAN connection provided by Cow's ISP,
and Platypus can reach E over the WAN connection in her dorm room.

Then, they can each "dig tunnels" to E.
Since E is just another node, it routes traffic from Cow to Platypus and vice versa,
connecting mesh A with mesh B.

### So, what's an exit node?
An exit node is just another node on the mesh!
There are only a few distinctions between exit nodes and normal nodes.
- An exit node has a public IP address on the public Internet in addition to its mesh address.
- An exit node is probably a fancy server, not home router.
- An exit node runs a special application - a Tunneldigger *broker*.

The broker application manages tunnels from other nodes to *link parts of the mesh together* and *route traffic between the mesh and the open internet*.

Of course, as a regular old node, it's also capable of meshing directly between other nodes without Tunneldigger
if it has a direct connection to the mesh.

### Summary
While exit nodes facilitate access to the larger internet, they also allow us to connect disparate parts of the mesh. This is accomplished by creating `l2tp` tunnels between nodes using tunneldigger.

For example, one could connect a home node's WAN port to the home router provided by a private ISP, at which point the home node could dig a tunnel over the open internet to an exit node. This tunnel would then allow the node to access other nodes on the mesh, and vice versa.
