# Questions

Let's keep track of our questions and our conversations about our questions.

If you think you kind of know an answer, but you're not sure, commit it! **Let this be a working document** of our attempts to feel satisfied in our understanding (i.e. learn) :-)

**Leave your (pseudo)name with your answer** so that each answer is **recorded as a dialog.**

Respond to questions and answers with more questions and answers!

You can also **leave a symbol of your intention to research a question** and return later with more words by committing your (pseudo)name below a question that is missing an answer.

**With every answer, include links to resources you used to develop your understanding. If you know something but do not know how you know it, it will still be useful to find and point to a resource that verifies your understanding.**

## Questions about computer networking in general

#### What is an ip address?

#### What is a mac address?

#### What is the OSI (Open Systems Interconnection) model?

#### What is a network interface (also called a network device)?
##### How many ip addresses can a network interface have? How many networks can an interface belong to?

#### What is a gateway address?
##### Is the gateway concept specific to IPv4 and its small address space? Do you still need gateways to route IPv6 traffic?
@bengo and @bennlich think you need gateways in both IPv4 and IPv6 networks. An IPv6 network is still a network of networks, so you still need gateways to route packets between adjacent networks. We think that w/o gateways, your routing table would need an entry for every computer on the internet (as opposed to a mapping from subnets -> IP addresses of gateway machines that know how to deliver packets within a certain subnet).

#### What is a subnet?
##### What is a subnet mask?

#### What is a bridge?

#### On Linux, what are the components of a route in a routing table?
##### Why does a route include a gateway address *and* and an interface if an interface already has an associated ip address?

#### How does traceroute work?

@wwwhtml can you clarify the next two questions a bit? I couldn't figure out how to phrase.

#### How Who makes the first call/connection client or DHCP or Router or who who :)

#### IP info pushed to clients [from where?] (IP, Subnet, GW, DHCP, DNS)



## Questions about the Oakland People's Open Network in particular

#### What is a home node?

#### What is an exit node?
##### If a home node is connected to more than one exit node, which one does it use?

#### What is babeld?
##### When does babeld use IPv6 vs IPv4?

#### What is tunneldigger? 
##### At a low level, what does it do? How does it send/receive packets?

