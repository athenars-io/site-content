This article about the [athenars sub-systems](https://athenars.io/the-athenars-sub-systems/) has been published.

> We break down the Athenars system into its five key sub-systems. Our system design starts at the high level then gradually builds out based on our high level requirements.

Before diving straight in to selecting specific components of the Athenars stack, we should consider higher level sub-systems aligned with our system requirements first. See the previous post for details of our overall system requirements.

As we continue to design more detailed parts of our system, and before we buy or download anything, we want to remain zoomed out and broad and consider our key sub-systems. Some sub-systems design decisions are more obvious with less options to consider, while some aspects have quite a range of different approaches one could take.

# Five key sub-systems

In the Athenars system, there are five key sub-systems that together form the whole. These five sub-systems were only arrived at after carefully considering how a complete system could best satisfy our needs. Already, decisions made here will impact the components, implementation and technologies used.

Here are the five Athenars sub-systems:

1. Gateway / firewall / router.
2. Hyper-converged compute / storage cluster.
3. IP Network.
4. Building automation bus system.
5. Electrical.

## The gateway sub-system

The gateway / firewall / router sub-system is that component that sits on the edge of our internal local network acting as a guard. It sits there on that wall, facing out, protecting our private network from the wild west that is the big bad internet. It controls the traffic that goes between our local network and the internet and vice versa. It is our *gateway*. It uses our firewall rules. It routes our traffic.

It can also do a lot more. It can block ads from the internet for all devices on our internal network. It can also provide proxy services we may have running in our system. This allows us to use sub-domains instead of IP addresses. This means we can go to nextcloud.domain.com instead of 192.168.1.34 which makes things much more human friendly. If we have the gateway sub-system capable of managing validated certificates, it also means we can go to https://nextcloud.domain.com so we can get that re-assuring padlock in our browser which also encrypts our traffic in transit protecting us from many man in the middle attacks.

Our gateway sub-system can see almost all of our local traffic. So it can also be a great data source to monitor the health and security of our system. So providing the tools to be able to access it, and being able to export and collect that data is important as well. We don't want to be forced to use additional systems via vendor upsells.

So our gateway sub-system is pretty important. While physically small, it has many important functions.

## Hyper-converged cluster

There are many ways to manage storage and compute in a given system. Most people just use laptops or desktops. Some have more powerful desktops called workstations. Some people even have Network Attached Storage (NAS) to make files like documents available to many devices on a network. A NAS typically also has some form of drive redundancy built in so that if any one drive fails, the system can continue to run with no loss of data. Replacing that drive before any others fail is usually all that is required.

Some people also use a server. This is typically a standalone computer, normally lower powered than a desktop computer, that is on 24/7 and serves some form of... services to users. This could be a file server or media server. These servers usually have more storage than is typically found on a desktop computer, and consumes less energy than a normal desktop computer. Servers are also typically higher powered than a NAS as they can run a much larger variety of services due to this.

Once people get used to having a NAS or server on their system, they typically start to find other uses for it. For example, people often find a need to store their personal photo library on a server. Likewise, storing their own videos is a typical use case. Having ones own photos and video locally is often a desire for people who enjoy photo or video editing.

As people seek to use their home services in new ways, typically a home network video surveillance camera system is attractive. This often involves setting up a number of power-over-ethernet (POE) cameras all feeding video into a central video surveillance program, often with person and car detection these days.

Other attractive uses includes storing their contacts and calenders locally and off the cloud providers systems. Personal task and project management, local chat, smart home automation and data visualisation are also appealing.

However, if any one NAS or server has a power supply, CPU, memory or motherboard problem, they can lose all data held on them. So even though they may have some redundancy and can lose one hard drive, they cannot tolerate any other part of their system failing. And even if they have good backups, replacing the failed system can take time - potentially even days. 

For people who become used to having access to their locally provided services, this can be very disruptive. This is why Athenars has opted to go for a *cluster* setup. We judge that with a certain software and technologhy stack, the added complexity is not too significant and the benefits far outweigh the comparitavely small complexity cost.

A properly configured highly available cluster will allow for not only a single drive in any one machine fail, it also allows for an entire machine to fail and we don't lose any data or services. In Athenars, we use a minimum of three servers, clustered together. This cluster shares both compute and storage across the cluster that provides *highly available* services. 

Being highly available means that if a machine fails, the services that were running on that system are automatically migrated / replicated to one of the remaining two servers in the cluster. The failed server is repaired or replaced, added back to the cluster and is brought back online and users accessing the services need not even know.

## IP network sub-system

Our IP network is mostly standard, with a few demands or implications due to the other sub-systems. As standard, our IP network is gigabit and we do use virtual local area networks (VLANs) to seperate some of our devices into their own isolated seperate virtual subnets. This is an important layer to security but it also helps to reduce potential congestion in our network activity which assists with performance. For VLANs, we will need to use managed switches.

One component of most Athenars systems will be a home security surveillance system, which will use POE Cameras powered by POE managed switches. These will all be on their own VLAN for not only security reasons, but also to move the traffic from the video streaming out to their own subnet and free up bandwitch for other devices, like media streaming devices.

The IP network will also connect to the home automation sub-system. It will obviously connect devices to the internet through the gateway sub-system. Because we will be using a compute and storage cluster, we will need an element of our IP network to be much higher in throughput than for other areas. We want high bandwidth between our servers in our cluster so that we can achieve as close to drive read and write speeds across our cluster as possible. We don't want the network to be the bottleneck.

This network speed and performance also creates new potential use cases. For example, it provides options for centralised high performance clusters with small and thin client devices that are only used to remote into the shared and powerful servers. While many people have negative experiences using workplace remote access services, these are typically deliberately provided in a cost effective manner. However with high-speed networking that is available for local networks, up to 100GB/s but also 25GB/s is often used, speeds can feel as fast as direct access to drives on a device.

# Building automation sub-system

A building automation sub-system is the aspect that connects various sensors to various actuators. For example, a motion sensor being triggered turns on a light. There are many options, and pitfalls, in this area. While there are many options, very few actually work well together. Some options can appear very appealing due to marketing, brand name or appearance. However it is often these highly marketed options that are the most locked down.

In Athenars, we want all control to be local. We want no vendor harvesting our data. We don't want to have any cloud account to operate devices on our local network. While wireless technology has come a long way, we want wired automation infrastructure for the ultimate in not only reliability, but also responsiveness and minimal latency.

The Athenars solution is seeking vendor neutral options with open protocols and open standards as a priority. While wired solutions are preferred, we want a wireless solution for applications where wired options are not feasible or desirable. Any solution, whether wired or wireless, should be vendor agnostic, use open protocols and be reliable and have no cloud accounts. For wireless systems, we also don't want to have to use more than one hub.

## Electrical sub-system

The electrical sub-system for an Athenars system is probably the most boring. The main area of focus for us, is we want to be able to access energy usage data. We also want to be able to integrate solar generation, not only for our data collection, and also connect to the IP network and the building automation sub-system.

The most unconventional element of the Athenars electrical sub-system is that our light switches do not need to have mains power run to them. If we can use our wired building automation system of choice, the automation bus system will connect to and power the switches. The actual switches, the actuators for the lights, will be centralised in a sub-board.
This centralisation of switching and other controls into a single board makes maintainance easy, as well as makes additional improvements and extensions more conveniant. It also happens to remove power from needing to be run into many walls to light switches.

For retro-fit options where bus-cabling cannot be run, alternative options that do use traditional mains wiring to wall switches can be utilised.

For solar power, while there are many vendors, we will select only the vendors who allow open access to their equipment and generated data and allow for local monitoring and control. For solar it is important to avoid vendor lock-in especially due to the costs associated with installation. Counter-intuitively, the vendors offering the most open systems will see them highly recommended by Athenars and will therefore be far more likely to see repeat business.

# The sub-systems interact

The gateway / firewall / router, IP network and electrical are the more obvious sub-systems. Most systems tend to require these sub-systems. Our options for how to deploy these sub-systems and how they are architectured and configured is where we arrive at a range of options.

Some of our other choices for sub-systems will influence how we implement these more obvious sub-systems. For example, our choice to utilise a hyper-converged cluster will influence how we deploy our networking and what components we choose to utilise. For our automation sub-system, how we collect data, utilise solar and integrate with the electrical sub-system is where we have many more design choices in accordance with our system requirements.

## Some buzzwords, but of substance

Any system like Athenars needs to be able to compute and process data. It also needs to store data. After much consideration, it has been become evident that the optimal way to meet these needs while most aligning with our overall requirements, is via a hyper-converged compute and storage cluster. This is key decision that takes advantage of a particular technology stack, which we'll dive into in the next posts. This particular sub-system will give us high availability for both compute and shared storage.

## Automation and the bus

There are many options for building automation from bus to IP to a range of wireless protocols. There are proprietary vendor locked options like Control 4 and Savant through to consumer oriented wifi devices that connect to cloud accounts. There are also other wireless protocols like Zigbee and ZWave. Newer consumer oriented Thread and Matter backed approaches are potential future solutions. However, for the optimum in performance, with the lowest latency, with the highest reliability, we have chosen a physical bus-centric automation sub-system. There are many advantages to this system which we'll get into in detail in the next section. And there is more to a building automation system than the communication medium. We'll get into the details in coming posts.

So that explains how we've taken our high level system requirements, then designed the various sub-systems within it. Already, these decisions are shaping what the Athenars technology stack will consist of. Already, the overall uniqueness of the Athenars approach is becoming evident and quite exciting.

Next, we'll talk about the various component options we considered for each sub-system and explain why we made the choices we did.

# Sneak peak at some key components

To ease the suspense, here are the main components we've selected for each sub-system.

Gateway / firewall / router:

- pfSense.

Hyper-converged highly available cluster:

- Proxmox and Ceph.

Networking:

- Microtik and Unifi.

Building automation bus.

- KNX.

Electrical:

- Victron, ABB.

Be sure to now learn why we made the choices we did. Within the documentation explaining why we selected each of the components within each sub-system, we also highlight some of the other key elements. These other elements include our selected databases as well as messaging and communication protocols and the like.

Additionally, a lot of research into the various options was conducted in our own homelab type of environment. Homelabs are a fantastic way to experiment and test various software on a day to day basis from a user perspective.
