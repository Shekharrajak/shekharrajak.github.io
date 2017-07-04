---
layout: post
sciruby_post: true
title: Coding Period Week - 3
week:  16 June 2017 - 22 June 2017
posted_on: 2 July 2017
type: post
categories: gsoc2017_post
permalink: /blog/GSoC-2017/:title
tags:
  - Open Source
  - GSoC
  - SciRuby
  - Daru
---


#### HighCharts and Nyaplotlibrary


##### 16, 17 June 2017 Report :

1. Added examples for using HighCharts library in daru-view . Almost all kind of chart examples: [http://nbviewer.jupyter.org/github/Shekharrajak/daru-view/tree/nyaplot_highcharts/spec/dummy_iruby/](http://nbviewer.jupyter.org/github/Shekharrajak/daru-view/tree/nyaplot_highcharts/spec/dummy_iruby/)

2. Most of the time I spent on Adding specs.

-------------------------------------------------

##### 18, 19 June 2017 Report:

- Added Sinatra app in spec/dummy_sinatra and updated the rails application in spec/dummy_rails

- Fixed some bugs and adding specs.

- Working on google charts tool.

- I got some difficulty in running matplotlib.rb gem in iruby notebook. I am discussing it in this issue : [https://github.com/mrkn/matplotlib.rb/issues/4](https://github.com/mrkn/matplotlib.rb/issues/4)

-------------------------------------------------

##### 21 June 2017 Report :

- Fixed rubocop error and rspec . It took time to fix rspec and rubocop errors.
- Working on google charts tool.
- Adding rake tasks, to update the JS files automatically.
- Fixed bugs.

-------------------------------------------------

##### 22 June 2017 Report :

1. Rake file added for highcharts and updated the readme.

2. Discussing about Nyaplot : can we use it offline ? In this issue :  [https://github.com/SciRuby/nyaplot/issues/5](https://github.com/SciRuby/nyaplot/issues/5)

3. Read some articles on Service worker in Javascript that can load webpage offline(just need the webpage to load once online). See this example : [https://googlechrome.github.io/samples/service-worker/basic/](https://googlechrome.github.io/samples/service-worker/basic/)  . May be it can be useful when user browser has already loaded the dependent JS files once through net and then it can be usable in future when user is offline .

-------------------------------------------------
