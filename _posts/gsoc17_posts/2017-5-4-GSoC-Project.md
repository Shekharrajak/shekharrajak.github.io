---
layout: post
sciruby_post: true
title: GSoC Application
week:
posted_on: 30 May 2017
categories: gsoc2017_post
type: post
permalink: /blog/GSoC-2017/:title
tags:
  - Open Source
  - GSoC
  - SciRuby
  - Daru
---


#### Getting up for Project

I started searching for the project and previous blogs in [SciRuby site](http://sciruby.com/blog/) and works done in previous GSoC. I found project "Make Daru more ready for integration with modern Web framework" good for me. I started discussion on this topic and prepared the proposal.


#### SciRuby/Daru

**Abstract of my application**

DaRu (Data Analysis in RUby) is a library for storage, analysis, manipulation and visualisation of data. Currently it is doing good job for scientific usage(in IRuby notebook), but if user want to visualize some data for integration into existing web application, then Daru methods have to output result/chart/graph/datatable such a way that output is directly usable into web application (in html file). Also Daru must have better import/export technique so that new importers/exporters can be defined easily. Mostly modern web application will use NoSql database, that is easy to scale. It will be very useful if Daru can connect with relational or non-relational database and make query operations easy. This project aims to make Daru more powerful for web application to use it as data analysis and visualisation tool, by working on above issues.


**Brief Overview**

Present days most of the people use Python or R languages as their data analysis tool. R has an edge in statistics and visualization, whereas Python has an advantage in machine learning and building tools through packages like NumPy and Pandas . Also Python can be used in web application to interact with a variety of databases, and manage users. When we think of Ruby to get these features, we see that, in web development Ruby on Rails is more popular than similar Python frameworks (e.g. Django and Flask). Ruby is also
the preferred language for DevOps related tasks (e.g Puppet and Chef). So Daru gem is very useful for data analysis projects.

My main intention is :
● To design and implement better `io` in Daru, so that new importers/exporters can be
easily defined.
● To design and implement interface for accessing different types of databases.
● To define and use other gems to get the charts/graphs in interactive html code , so
that they can be used in web pages directly. Current Daru visualisation abilities
target scientific usage, they can be used to understand data in IRuby notebooks. But,
when we want to visualize some data for integration into existing web application
then Daru fails to provide good html code.


#### Discussions


● Mailing list : [https://groups.google.com/forum/#!topic/sciruby-dev/iIKZMRVydgo](https://groups.google.com/forum/#!topic/sciruby-dev/iIKZMRVydgo)

Other discussions :

● [https://groups.google.com/forum/#!topic/sciruby-dev/wcnFC824nJg](https://groups.google.com/forum/#!topic/sciruby-dev/wcnFC824nJg)
● [https://groups.google.com/d/msg/sciruby-dev/Z70Tj70TdeQ/_ZNOXkDUFwAJ](https://groups.google.com/d/msg/sciruby-dev/Z70Tj70TdeQ/_ZNOXkDUFwAJ)


#### Project link :

[google Docs link](https://docs.google.com/document/d/1IfuciZFVBObzRy1t7hpNyXl8Cs4brwlRKYOo4g8AhX4/edit?usp=sharing)


#### And the happiest moment of this journey is seeing the name twice in GSoC site

<div class="result"> <img src="{{ site.baseurl }}/images/img/result_gsoc17.jpg"/>  </div>

#### My revised proposal :

SciRuby community divided works for 2 peoples (me and Athitya) on this project and my work is to create `daru-view` gem (a plugin gem) which will be mainly for presenting and visualizing data.

[My revised proposal link](https://docs.google.com/document/d/1Y6UwpiDJXcRfgUbmpZM6Qs9cl2TmtCmbh_C_VwtRYiM/edit?usp=sharing)

-------------------------------------------------
