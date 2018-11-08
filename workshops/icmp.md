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

How does traceroute work? Does the output include entries consisting only of asterisks/stars? What do those mean?
