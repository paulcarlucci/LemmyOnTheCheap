# LemmyOnTheCheap
For when you want to host your own Lemmy in a sane fashion but you're not exactly VC backed.

Step Zero: Get a host

You can certainly host this at home with some kind of Linux box, but unless you've got a static IP address then you're going to have issues.  Also, the connectivity you've got at home is absolutely not the same, even if you've got a fiber pipe it's very very unlikely to be peered with multiple backbones like a cloud provider is.

In the spirit of On The Cheap you're going to want to get an Oracle Cloud account.  "Alright, I'll go get an Ora... wait WHAT!?!"

No really, OCI is currently the S-Tier of free cloud accounts.  Their always free offering includes a VM sporting 4 ARM64 cores, 24 GB of RAM, and 200 GB of disk.  You can also get two more VMs running an eighth of an x86 vCPU to use as bastion hosts but you have to split out a minimum of 50 GB of disk per host and that's just not worth it.

https://www.oracle.com/cloud/free/

They also include a number of other free services, of which we'll be touching as little as possible.  The idea of this guide is to self-host everything on one box so you can pull stakes if you need to and drop it anywhere.  For the rest of this guide I'll assume you've done the same though it won't really matter if you do.  Quick note about OCI, wherever you pick your "home" data center to be that's where you'll be stuck unless you pay for stuff, so choose wisely and well.

You will still need to pay for a domain name and possibly DNS hosting.  For a myriad of very good reasons I strongly recommend not self-hosting DNS, it's half a buck a month at AWS or even free at the likes of DollarDNS and Aftaid.net and reliability is key here.  You don't DNS lookups to completely fail just because your host is down.

http://www.dollardns.net/compare.html

You need multiple nameservers which should be on diverse networks.  AWS Route53 gives you that as a service though you certainly can pull that off with having each nameserver on a separate free provider.  I'll let you fill in your own blanks here in registering a domain as there are plenty of guides out there given this is as generic a topic you can get in the world of hosting stuff.
