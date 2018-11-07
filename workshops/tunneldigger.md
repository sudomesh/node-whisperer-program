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
