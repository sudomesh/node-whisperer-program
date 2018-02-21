# Welcome To The Node Whisperer Program

Node whisperers explain how (exit/home) nodes work and keep them from misbehaving by troubleshooting, preparing bug fixes, applying patches, implementing new features and upgrading software. To become a node explainer, you should be able to show someone how to build your own internet by configuring one, (ideally two) home node(s) (https://peoplesopen.net/walkthrough ) to use a custom, self-created exitnode (https://github.com/sudomesh/exitnode ). This also includes showing how babeld and tunneldigger work together by using (and improving!) https://github.com/sudomesh/babeld-lab and https://github.com/sudomesh/tunneldigger-lab on the home and exit nodes using tools like ip route , ip addr, tcpdump . 

Existing node whisperers include @juul , @paidforby and @jhpoelen - talk to them if you'd like to learn how to whisper too.

## concepts
1. basic understanding of ip addresses, internet routing, osi model.

## exercises 

ingredients (internet-in-a-box?)
a) laptop with ethernet port
b) 2 homenodes 
c) 1 exitnode (locally/remote)

1. re-enact packet routing in person by passing pieces of around (needs links)
2. show packets arriving at an exit node 
3. trace packets from a laptop, via a home node to an exit node to the "internet"
4. draw the topology of the mesh network using the routing table
5. draw the paths packets take in the topology using traceroute 
6. turn off babeld on both home node and exit node, and use "ip" to manually create routes, recreating the path as seen in 3.
7. describe the steps you would take to debug a peoplesopen ssid that does not provide a path to the internet. 
8. same as 7. but then a path to other home nodes.
9. login to a homenode via a exit node
10. login to a homenode via public ssid
11. re-start tunnel digger (following tunneldigger-lab)
