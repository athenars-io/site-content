# Athenars hyper-converged infrastructure sub-system

Athenars had decided to utilise *Proxmox and Ceph* in our technology stack. To better understand how our decision fits into our overall design, please see our other posts on our [system requirements](https://athenars.io/defining-the-requirements-of-the-athenars-system/) and considered [sub-systems](https://athenars.io/the-athenars-sub-systems/).

This will not be a blow-by-blow feature comparison. We will however walk through and explain our reasoning for choosing Proxmox and Ceph over the other options. A lot of this won't be surprising when considering our system requirements provided in the previous posts.

First, here are the main options that were considered.

- Proxmox and Cepth.
- TrueNAS Scale.
- Unraid.
- XPC-ng.
- VirtualBox.
- Synology VMM.
- VMware esxi.

# Main feature requirements

We have specific wants and needs for this sub-system. In the end,our decision to use Proxmox was fairly easy once we laid things out. The main features we wanted in our hyper-converged infrasture sub-system are as follows:

- we would prefer to use open source software.
- we would prefer a mature platform.
- we want a solid platform for virtual machines.
- we want a solid platform for containers.
- we want a platform that can be clustered.
- we want a platform that can be deployed highly available.
- we want a well integrated shared storage solution.
- we want good backup options.
- we want a system built on Linux.
- we want to be able to access the data that is available in the cluster.
- we want to be able to get the data out of our cluster for longer term storage and analysis.
- we want a convenient graphical user interface.
- we want open licenses.
- we want hardware freedom.
- there should be broad hardware support
- it should not require a cloud account.
- functionality should not be locked behind additional licenses.
- it should be user-friendly.
- there should be a community around it.
- there should be good documentation.
- we would prefer to be able to utilise file, block and object storage.
- we would prefer a range of file system options.
- we would prefer flexible virtual networking options.
- there should be no major concern around the long-term development of the chosen platform.

What isn't critical in this Athenars sub-system are more enterprise features like multi-site management. These are not required at all for our purposes. Athenars does not intend on actively managing systems as the intent is that people will maintain their own systems.

## The best fit for our wants and needs

For our requirements, by far, the most suitable platform is Proxmox. It basically ticks all the boxes.

There are other decent options. There are actually quite a lot of available options. However some have very small communities around them, poor or little documentation and their ongoing long-term use is doubtful. The proprietary options are not good options due to having so many limitations around how they can be used. For Athenars needs, Proxmox (especially with Ceph), is our clear choice.

https://youtu.be/GMAvmHEWAMU

We think the above listed features will provide a solid hyper-converged, highly available cluster capability. We should probably now talk a little bit more about the specific design thinking and intended configuration for our Proxmox / Ceph hyper-converged highly-available cluster. Details will be explored in more detail in future posts.

## The design of the cluster

Any Athenars cluster will have three servers at a minimum, clustered together via Proxmox. These servers should be as low power and energy efficient as possible, while still allowing the ability to have at least one NVME drive and one SSD drive (though preferably more) and also allow for 1 x 25GB/s network interface card (NIC), 1 x 10GB/s NIC and preferably one out of band remote management port.

The 25GB/s NIC is to allow for network speeds that are close to the read and write speeds of SSDs. This specific network is for Ceph internal private storage networking. The 10GB/s NIC is for connection to end user devices. 10GB/s networking is more easily obtained, is close to HDD read and write spees while allowing for better more native feeling remote access, compared with 1GB/s NICs. We note that both 25GB and 10GB is for internal networking only. For most people, 1G speeds is all that is possible for internet / ISP connections.

This three node configuration allows for optimal Cepth deployments within reason. The Ceph shared storage across the cluster can be used by both Virtual Machines (VMs) and LXC Containers (CTs). This shared storage means we can have automatic failover for both VMs and CTs in Proxmox, noting that CTs share the kernel with the host so they are not as quick to transition to another node upon node failure.

Our cluster configuration with Ceph storage means we don't need to use a NAS for shared storage to allow for high availability. This removes the negative single point of failure in such a setup. However we can now use a NAS for a local backup destination. Alternatively, we could build a seperate small Proxmox Backup Server (PBS).

> Proxmox (with Cepth) is our hyper-converged, highly available, virtualisation and containerisation cluster platform of choice.

We also like that Proxmox has support subscriptions available. It's nice to have a clear way to support the open source project and actually get help if you need it from the ultimate experts in the system.

## Conclusion

That concludes our logic and reasoning for selecting Proxmox (with Ceph) as our hyper-converged cluster sub-system for Athenars. It is a mature, actively developed, capable and powerful platform with hardware freedom.