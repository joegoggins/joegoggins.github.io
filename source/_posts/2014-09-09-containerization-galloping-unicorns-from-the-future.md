---
layout: post
title: "Containerization: Galloping Unicorns from The Future"
date: 2014-09-09 12:19:24 -0500
comments: true
categories: 
---


Containerization is a galloping unicorn from the future of cloud operations. In it's bursting saddlebags it posesses magic relics to:

1. eliminate the pain of setting up application development environments
2. drastically reduce the time it takes to spin up cloud infrastructure for production, testing, high-availability, or auto-scaling
3. decrease cloud operating costs by piling many containers onto single virtual machines instead of individual [under-utilized] machines.
4. improve security by isolating application processes further with containers
5. facilitate rapid sharing of complex infrastructure across cloud providers.

But **it's not the end all be all and in many of these promises it's still quite rough around the edges**. It should DEFINITELY be a huge part of your medium and long term roadmaps, but if you're thinking you can swoop through and realize value in your organization from all of these in a couple of days, you have another thing coming.  Here's a list on my take of each of these areas with 

### 1. eliminate the pain of setting up application development environments

These two articles ([1](http://www.talkingquickly.co.uk/2014/06/rails-development-environment-with-vagrant-and-docker), [2](https://blog.abevoelker.com/rails-development-using-docker-and-vagrant) ) do an excellent job explaining how you go about building a Docker + Vagrant workflow to build a portable Rails environment. Though they certainly exhibit some great capabilities, if you have a team that doesn't spin up local VM's regularly, rough edges of using boot2docker (like it's special IP, it's sideloaded VM, and the `DOCKER_HOST` env var to name a few) can burn you and result in a lot confusion and time spent troublingshooting the "portable painless dev env".

It's still worth pursuing because the container/virtualization knowledge gained is valueable. But it's not gonna happen instantly.

### 2. drastically reduce the time it takes to spin up cloud infrastructure for production, testing, high-availability, or auto-scaling

For production container usage, [Chef-DK](https://downloads.getchef.com/chef-dk/) + [knife-container](https://github.com/opscode/knife-container) are the jam. However, more a still beta and their actual functionality is fairly limited, you still need to know a bunch about Docker to really do something cool here.

For infrastructure testing, [Test-Kitchen](http://kitchen.ci/docs/getting-started) + [kitchen-docker](https://github.com/portertech/kitchen-docker) are incredible. However, it's no small feet to get the prerequisite testing harness/infrastructure up before it can deliver on the dream of spinning up entire clusters as containers, running tests, and destroying them in seconds rather than minutes.

### 3. decrease cloud operating costs by piling many containers onto single virtual machines instead of individual [under-utilized] machines.

I drool over [CoreOS](https://coreos.com/). An amazing Docker enabled technology that combines 

- the [best] init + process supervision system in existence that most major linux distributions (including Ubuntu) are switching to ([systemd](http://www.freedesktop.org/wiki/Software/systemd/)),
- [etcd](https://coreos.com/using-coreos/etcd/) a high-available key value config +service discovery tool for clusters, 
- and [fleet](https://coreos.com/docs/launching-containers/launching/fleet-example-deployment/) an amazing tool that makes systemd behave sensibly + intelligently across a cluster of containers.

Of all the magical goodies the containerzation unicorn brings, this is the one I'm currently most stoked about.  It's also a paradigm rethink and thus for most cloud ops shops, it's a big endeavor.

### 4. improve security by isolating application processes further with containers

Yep. It's great that tools like [chef-container](https://docs.getchef.com/containers.html) strip out all of the important encryption and auth settings when spinning up new docker container.

Again, this tech is still bleeding beta software. Furthermore, there is still a lot of uncertainty as to what the best practices are for running hybrid configurations that combine the idea of [immutable infrastructure](http://www.getchef.com/blog/2014/06/23/immutable-infrastructure-practical-or-not/), (also see [1](http://chadfowler.com/blog/2013/06/23/immutable-deployments/),[2](http://blog.codeship.io/2013/09/06/the-codeship-workflow-part-4-immutable-infrastructure.html)) that Docker espouses mixed with some of the dynamism of Chef.  It's something to play with and figure out over the next couple of months.

### 5. facilitate rapid sharing of complex infrastructure across cloud providers.

[DockerHub](https://hub.docker.com/) is RAD! GitHub for complex OS images.  Who is gonna argue with that?

Though there are some good images out there, without established norms about how to guarantee a published image is built a certain way, I have a hard time not viewing this as an attack vector analogous to a site or email that wants you to download and execute a malicious binary to your computer.  Given the number of smart people pouring into this space, I would expect this area to mature rapidly. Also, as the community grows the robustness of the peer review system will improve.
