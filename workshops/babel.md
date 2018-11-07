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

