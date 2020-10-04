---
layout: post
conf_post: true
title: ApacheCon North America 2020 Talk 2
posted_on: 4 Oct 2020
categories: conference
type: post
permalink: /blog/Talks/ApachCon/:title
background_image: cm-apachecon.png
tags:
  - Open Source
  - Apache
  - ApacheCon
  - BigData
  - Kubernetes
  - talk
  - YARN
  - Spark
  - Mesos
  - ClusterManagement
  - Docker
  - Container
---


#### ApacheCon @Home 2020



-------------------------------------------------

#### Title: Cluster Management in Apache Ecosystem & Kubernetes

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Join me <a href="https://twitter.com/ApacheCon?ref_src=twsrc%5Etfw">@ApacheCon</a> Events : <a href="https://t.co/GoKWvYXeEe">https://t.co/GoKWvYXeEe</a><br><br>Talk title: <a href="https://twitter.com/hashtag/Cluster?src=hash&amp;ref_src=twsrc%5Etfw">#Cluster</a> Management in <a href="https://twitter.com/hashtag/Apache?src=hash&amp;ref_src=twsrc%5Etfw">#Apache</a> Ecosystem &amp; <a href="https://twitter.com/hashtag/Kubernetes?src=hash&amp;ref_src=twsrc%5Etfw">#Kubernetes</a> <br><br>Time: 1 AM IST (12:30 PM PST)<a href="https://twitter.com/TheASF?ref_src=twsrc%5Etfw">@TheASF</a> <a href="https://twitter.com/ApacheCommunity?ref_src=twsrc%5Etfw">@ApacheCommunity</a> <a href="https://twitter.com/ApacheSpark?ref_src=twsrc%5Etfw">@ApacheSpark</a> <a href="https://twitter.com/ApacheMesos?ref_src=twsrc%5Etfw">@ApacheMesos</a><a href="https://twitter.com/hashtag/clustermanager?src=hash&amp;ref_src=twsrc%5Etfw">#clustermanager</a> <a href="https://twitter.com/hashtag/resourcemanagement?src=hash&amp;ref_src=twsrc%5Etfw">#resourcemanagement</a> <a href="https://twitter.com/hashtag/apachespark?src=hash&amp;ref_src=twsrc%5Etfw">#apachespark</a> <a href="https://twitter.com/hashtag/apachecon?src=hash&amp;ref_src=twsrc%5Etfw">#apachecon</a> <a href="https://twitter.com/hashtag/kubernates?src=hash&amp;ref_src=twsrc%5Etfw">#kubernates</a> <a href="https://t.co/oTKRtCvJyg">pic.twitter.com/oTKRtCvJyg</a></p>&mdash; Shekhar Prasad Rajak (@Shekharrajak) <a href="https://twitter.com/Shekharrajak/status/1311369921364779008?ref_src=twsrc%5Etfw">September 30, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


##### Abstract

Apache have powerful cluster & resource manager already, so do we really need to use Kubernetes for the deployment while using Apache projects ?

Let's find out what type of cluster management system Apache already have ,How cluster management works in each of below cases and when we don't need any other cluster management top of it and when we can leverage the power of both this apache cluster modes and Kubernetes in resource & cluster management.

* Apache Spark Standalone: A simple cluster manager available as part of the Spark distribution..

* Apache Mesos: A general purpose distributed OS level push based scheduler & resource manager.

* Apache Hadoop YARN: A distributed computing framework for monolithic job scheduling and cluster resource management for Hadoop cluster (Apache/CDH/HDP)

We will see some benchmarks and features that kubernetes can provide but it is not present(or not mature enough) in the Apache ecosystem, but still using, one or both can improve the performance.

We will deep dive into fundamentals of Kubernetes and Apache distribution, resource & cluster management system, Job scheduling, to get clear cut idea behind both ecosystems and why they are best in particular cases like Big Data, Machine Learning, Load balancer, and so on.

Applications are containerised in Kubernetes Pod, Kubernetes Service is used as Load balancer, Kubernetes High availability is because of distribution of Pods in worker nodes, Local Storage, Persistent volume & Networking and many other features will be compared side by side with Apache Ecosystem.
Like in Mesos, Application Group models dependencies as a tree of groups and Components are started in dependency order, Mesos-DNS works as basic load balancer, applications distribution among slave nodes, two-level scheduling mechanism, modern kernel "cgroups" in Linux & "zones" in Solaris, and so on.

Along with the comparison & benchmark the talk will provide practical guide to use the Apache project with Kubernetes. Audience will understand the Software System design and generic problems of processing the request through the cluster & resource managers and why it is important to have modular, micro service based, loosely coupled software design, so that it can easily go through the container or OS level cluster management systems.


This talk is clearly not to show who is winning but how can you win in your time, in the dark situation.




-------------------------------------------------
