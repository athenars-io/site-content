# Athenars hyper-converged infrastructure sub-system

Athenars had decided to utilise *Proxmox and Ceph* in our technology stack. To better understand how our decision fits into our overall design, please see our other posts on our [system requirements](here) and considered [sub-systems](here).

This will not be a blow-by-blow feature comparison. We will however walk through and explain our reasoning for choosing Proxmox and Ceph over the other options. A lot of this won't be surprising when considering our system requirements provided in the previous posts.

First, here are the main options that were considered.

- Proxmox and Cepth.
- TrueNAS Scale.
- Unraid.
- XPC-ng.
- Linux with Syncthing.
- VirtualBox.
- Synology VMM.
- Xen Project.
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
- there should be no major concern around the long term development of the chosen platform.
- we want open licenses.
- we want hardware freedom.
- there should be broad hardware support
- it should not require a cloud account.
- a range of local and distributed storage file system / storage options should be available.
- funcationality should not be locked behind additional licenses.
- it should be user-friendly.
- there should be a community around it.
- there should be good documentation.
- we would prefer to able to utilise file, block and object storage.
- we would prefer a range of file system options.
- we would prefer a range of virtual networking options.
- there should be no major concern around the long-term development of the chosen platform.

What isn't critical in the Athenars system are more enterprise features like multi-site management.

## The best fit for our wants and needs

For our requirements, by far, the most suitable platform is Proxmox. It basically ticks all the boxes.

There are other decent options. There is actually quite a lot of variety in the available options. However some have very small communities around them, poor or little documentation and their ongoing long-term use is doubtful. The proprietary options are not good options due to having so many limitations around how they can be used. For Athenars needs, Proxmox (especially with Ceph), is our clear choice.

https://youtu.be/GMAvmHEWAMU

We think the above listed features will provide a solid hyper-convered, highly available cluster capability.

> Proxmox (with Cepth) is our hyper-converged, highly available, virtualisation and containerisation cluster platform.

We also like that Proxmox has support subscriptions available. It's nice to have a clear way to support the open source project and actually get help if you need it from the ultimate experts in the system.

## Conclusion

That concludes our logic and reasoning for selecting Proxmox (with Ceph) as our hyper-converged cluster sub-system for Athenars. It is a mature, actively developed, capable and powerful platform with hardware freedom.