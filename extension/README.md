# Welcome to the Extended Extender Node Whisperer Extension Program

In this extesion, you will learn how to whisper to extender nodes. Extender nodes are essentially roof mounted antenna, though more accurately they are small, weatherized routers with an intergrated, often directional, antenna. These little roof mounted nodes are curcial in building a mesh network of any reasonable size. 

# Sudo Mesh Test Bed

This setup creates a small scale point-to-point link that easily fits within a room, or even a box.  

Necessary material:  

* a computer capable of ssh
* two MyNet N600 routers
* two Ubiquiti Nanobridge M5 routers/antennas
* two Power-over-Ethernet(PoE) adapters

First flash the routers with the instructions provided at https://peoplesopen.net/walk    

Next, mount one of the Nanobridge antenna (with it's dish) in one corner of a room, ideally close to wherever you get your internets (e.g. your home router, a wall jack, a server rack).  

Power the Nanobridge using the PoE adapter and connect one of the N600 routers to the LAN port of the PoE through port 1 or 2.  

Plug a tube of internet into the port labeled "internet" on the N600, we will call this router `Cow`.  

Now, mount the other Nanobridge on the opposite end of the room, far from the internets.   

Also power this Nanobridge using the PoE adapter and connect the other N600 router to the LAN port of the PoE through port 1 or 2. Let's call this router `Chicken`.   

The one problem with this setup right now is that the two N600s probably will be simply meshing with one another and ignoring the extender node connection. This is because they have their own ad-hoc interfaces that automatically mesh with each other. Rather than trying to turn of this ad-hoc feature, it is much easier to just change the BSSID of the ad-hoc network.  

To do this ssh in to `Chicken` by connecting to one of its wireless networks or directly through ethernet. Once in, edit the file `/etc/config/wirless` and find the option that reads `option bssid 'CA:FE:C0:DE:F0:0D'` and change it to something like, `option bssid 'CA:FE:C0:DE:F0:01'`, there are two occurances (one for the 2.4Ghz radio and one for the 5Ghz) so make sure to change both.

And that's it, assuming that your Nanobridge's are pointing at one another, you should not be able to hop to the internet through this connection. Try running something like, `traceroute 8.8.8.8` and watch the IPs hop from `Chicken`'s extender node to `Cow`'s extender node to `Cow` then to the exit node (or maybe there's another hop in between) and then off in the great unknown of the Internet.   
