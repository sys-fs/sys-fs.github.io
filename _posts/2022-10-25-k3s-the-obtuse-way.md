---
layout: post
title: k3s, the obtuse way
categories: [Kubernetes]
---

I acquired some old Raspberry Pi 3s through work and a housemate, so I thought
I'd put them to use to try out Kubernetes. Looking around, I found that k3s is
a good option for low resource environments. Unfortunately I think I might have
been _too_ low on resources! Upon getting the main server installed the CPU
load jumped to around 15. After applying the [iptables
fix](https://docs.k3s.io/advanced#additional-preparation-for-debian-buster-based-distributions)
from the docs, as well as [this
fix](https://github.com/k3s-io/k3s/issues/294#issuecomment-670372870) from a
GitHub issue, load still hovered around 8 and I was unable to get an agent to
join the cluster. I think that SD card performance may have played a part too.

As I'd already spent a day trying to get k3s running on the Pis, I decided to
go with the boring option and use my desktop to run k3s instead. After a quick
search, I found [this
article](https://itnext.io/how-to-create-kubernetes-home-lab-on-an-old-laptop-1de6cc12c13e)
on doing it with [Multipass](https://multipass.run/). 30 minutes later, I had
k3s running with one server and two agents. Nice. Shame about the Pis
though. Maybe they can be used for learning ARM assembler or something,
whenever I get around to Computer Organization & Design.
