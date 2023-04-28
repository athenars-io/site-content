This article about the [gateway sub-system](https://athenars.io/gateway-sub-system/) has been published.

# Athenars gateway sub-system

We have decided to utilise *pfsense* in the Athenars technology stack. The gateway / firewall / router sub-system is a critical piece of a holistic system so this was a really important decision. For abreviations sake in this article, we'll refer to this sub-system as our *edge* sub-system. To better understand how our decision fits into our overall design, please see our other posts on our [system requirements](https://athenars.io/defining-the-requirements-of-the-athenars-system/) and considered [sub-systems](https://athenars.io/the-athenars-sub-systems/).

This will not be a blow-by-blow, feature comparison. We will however walk through and explain our reasoning for choosing pfsense over the other options. A lot of this won't be surprising when considering our system requirements provided in the previous posts. Importantly, we developed our requirements and needs first, then sat back and considered the options.

# The options

Here are the main options that were considered.

- pfsense
- OPNsense
- Microtik RouterOS
- Unifi
- Sophos Firewall Home Edition
- Untangle / Arista NG Firewall Complete

## Main feature requirements

We have specific wants and needs for this sub-system. In the end, our decision to use pfsense was fairly easy once we laid things out. The main features we wanted in our edge sub-system are as follows:

- we would prefer to use open source software.
- we would prefer a mature platform.
- we would like to be able to handle (preferably Lets Encrypt) certificates.
- we would prefer to be able to use wireguard as our VPN of choice and have it on our edge sub-system.
- we would prefer to have a proxy on the *edge*.
- we want it VLAN capable (most or all modern gatways etc are VLAN capable, but we need to mention it explicitly regardless).
- we would prefer to have ad-blocking in our edge sub-system.
- we want to be able to have IDS/IPS in our edge sub-system.
- we would prefer if it was extensible where we can add functionality.
- the edge sub-system should be DNS capable (a simple functionality, but still we should include it).
- we want to be able to access the data that is available to an edge sub-system.
- we want to be able to get the data out of our edge sub-system for longer term storage and analysis.
- there should no major concern around the long term development of the chosen platform.
- we would prefer to be able to enrich our network data with geospatial data from IP data.
- the chosen features like IDS/IPS, proxies etc should all be known projects, not obsure, proprietary or otherwise unclear.
- not essential, but nice to have, the platform should be able to be virtualised for added redundancy (the Athenars system will not include physically redundent edge hardware).

What isn't considered critical in the Athenars system are more enterprise features like multi-site management. While redundancy in many parts of the Athenars system has been considered, we didn't consider WAN failover even though pfsense does have that option. This is one area where we drew the line between redunancy and added complexity and cost. Much of our functionality is from data held on our own site, so this mitigates the need to access the web and having WAN failover to a degree. The main concern is if we are away from our home location and want to be able to remote in via wireguard VPN when our WAN is down for some reason.

## Ticking boxes

For our requirements, by far, the most suitable platform is pfsense. It basically ticks all the boxes.

None of the other options are bad. They all have their strengths. Some might be particularly more attractive if you wanted to manage multiple sites. Depending on your use cases and requirements, some of the other options may be best. But for the Athenars needs, pfsense is our clear choice.

If you'd like to see a somewhat detailed feature-by-feature break-down of the various options, you could have a look at a video from Tom at *Lawrence Systems* in the following video.

https://www.youtube.com/watch?v=0bTjibLYSOo

For clarities sake, Tom is a long-term user and recommender of pfsense. Additionally, I've personally been using pfsense in my own home network for some years, so I too may be bias and my use of pfsense may have shaped what features I see as important for being in an edge sub-system. Regardless, pfsense is a great choice to meet the desired needs for the Athenars sub-system.

We think the above listed features are a great and natural fit for an edge sub-system. Also, having all of the listed features in the edge sub-system means we don't need to deploy them in our hyper-converged cluster.

## Packages

Some of the great packages we enjoy using in pfsense include:
- acme
- arpwatch
- haproxy
- nmap
- ntopng
- pfblockerng
- suracata
- telegraf
- wireguard

There are many others of course, and this is one of the main reasons we are comfortable including pfsense as our edge sub-system of choice in the Athenars stack.

We also like that there is a company behind pfsense (Netgate) and that it is possible to support ongoing development by purchasing their hardware that comes with pfsense pre-installed. However one can still install pfsense on whatever hardware we want. So that freedom is nice, and important.

# Conclusion

That concludes our logic and reasoning for selecting pfsense as the gateway / firewall / router / edge sub-system. It is a mature, actively developed, capable and extensible platform with hardware freedom.
