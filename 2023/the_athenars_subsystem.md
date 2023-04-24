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

The gateway / firewall / router, IP network and electrical are the more obvious sub-systems. Most systems tend to require these sub-systems. Our options for how to deploy these sub-systems and how they are architectured and configured is where we arrive at a range of options.

# The sub-systems interact

Some of our other choices for sub-systems will influence how we implement these more obvious sub-systems. For example, our choice to utilise a hyper-converged cluster will influence how we deploy our networking and what components we choose to utilise. For our electrical sub-system, how we collect data, utilise solar and integrate with the building automation system is where we have many more design choices in accordance with our system requirements.

## Some buzzwords, but of substance

Any system like Athenars, needs to be able to compute and process data. It also needs to store data. After much consideration, it has been become evident that the optimal way to meet these needs while most aligning with our overall requirements, is via a hyper-converged compute and storage cluster. This is key decision that takes advantage of a particular technology stack, which we'll dive into in the next posts. This particular sub-system will give us high availability for both compute and shared storage.

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
