---
layout: post
sciruby_post: true
title: Coding Period Week - 1
week:  30 May 2017 - 6 June 2017
posted_on: 6 June 2017
type: post
categories: gsoc2017_post
permalink: /blog/GSoC-2017/:title
tags:
  - Open Source
  - GSoC
  - SciRuby
  - Daru
---


#### Created daru-view repo and setup


##### 31 May 2017 :

1. Created daru-view repo and edited some files : [https://github.com/Shekharrajak/daru-view](https://github.com/Shekharrajak/daru-view)

2. Started working on Nyaplot in daru-view for web application. When I started defining modules and classes, I finalised the design pattern to use, after reading many articles . I think  Adapter design pattern and Composite design pattern is good for it.

_Why [Adapter design pattern](https://www.sitepoint.com/using-and-testing-the-adapter-design-pattern/)_ :

- Adapter pattern's motivation is that we can reuse existing gems if we can modify the interface.
- Using Daru-view join functionalities of independent or incompatible interfaces of different gems.

_Why [Composite design pattern](https://medium.com/@dljerome/design-patterns-in-ruby-composite-e815a25467b5)_ :

- Define common objects and use it for defining composite objects.

Let me know if you have any good links to understand how to design a good gem.

I am adding Nyaplot library and defining helper methods.


##### 1 June 2017  :

1. Setup the rspec, travis, simplecov .
2. Started working on Nyaplot library.  Defined class Plot . First adapter will be set, to use in plotting. Then require that adapter module to use its method in plot class .

```

|-- view
|   |-- adapters
|   |   |-- nyaplot
|   |       |-- some helper modules
|   |   -- nyaplot.rb
|   |-- plot.rb

```
Some thoughts :
---
Since daru already using Nyaplot library so I think we should use it directly `df.plot options` and `vec.plot options `. User must aware of options that is available in Nyaplot . Mandatory options are :

for dataframe = type, x, y
for vector = type

other options like height, weight, zoom, legend, etc can be setup using something like this :

```
        plot.configure do
          width(700)
          height(700)
            .....
        end
```
If any options is not defined then it will raise error (option is not available in that library).

For web application :

```
 div, script = components(plot)
```

script must be written in head tag and `div` in the body tag. Template is created created to generate script separately and body part using generate_body method.


##### 2 June 2017 report


1. Continue on nyaplot and added some highcharts templates to generate html code, scripts. I will finish them in this PR : [https://github.com/Shekharrajak/daru-view/pull/3](https://github.com/Shekharrajak/daru-view/pull/3)

2. It took me time to understand how IRuby notebook able to plot the charts using only the body div part generated in Nyaplot plotting system. I found that there is `to_iruby` and `show` in Nyaplot/frame.rb added by PR https://github.com/domitry/nyaplot/pull/8/files  and [this commit](https://github.com/SciRuby/nyaplot/commit/662ebc60b0d1e9fbebe7e06530d8450d266ebbdd) . I think IRuby.display (used in nyaplot `show` method ) uses `to_iruby`  . I will try the same with highcharts tomorrow.

3. [lazy_high_charts](https://github.com/michelson/lazy_high_charts) gem is created for generating charts in web applications. so it can't be used in IRuby notebook directly. I have discussed about it in this issue : [https://github.com/michelson/lazy_high_charts/issues/235](https://github.com/michelson/lazy_high_charts/issues/235) .I hope it will be fixed soon.

##### 3 june 2017 Report :

1. I have added dummy_rails app in spec folder, that will contain all the plotting features examples. Right now I have added Nyaplot examples . The commit link : [https://github.com/Shekharrajak/daru-view/pull/3/commits/f173906feccef737bc90ae42ffcfa967df3d315c](https://github.com/Shekharrajak/daru-view/pull/3/commits/f173906feccef737bc90ae42ffcfa967df3d315c)

2. I found that lazy_high_charts gem is not able to plot in IRuby notebook . I discussed about it in this issue : [https://github.com/michelson/lazy_high_charts/issues/235](https://github.com/michelson/lazy_high_charts/issues/235) and fixes the issue in this PR : [https://github.com/michelson/lazy_high_charts/pull/236](https://github.com/michelson/lazy_high_charts/pull/236)

I hope it will be merged and we will be able to use it in daru-view.


##### 5 June 2017 report :

1. Wrote blog post : [http://shekharrajak.github.io/gsoc_2017_posts/](http://shekharrajak.github.io/gsoc_2017_posts/) . I will add more contents soon.

2. In daru-view spec/dummy_rails app I got some error. I found that there is little problem in generating `div` part of the chart by Nyaplot, so it is just showing border of the chart in rails app (It works fine in IRuby notebook). Also it works fine when I used Nyaplot gem directly in web application. I hope it will be fixed soon.

3. Designing a good method to get chart using Highcharts that will help to pass options and data from daru dataframe, vectors to highcharts. Pr : [https://github.com/michelson/lazy_high_charts/pull/236](https://github.com/michelson/lazy_high_charts/pull/236) to get the chart in IRuby from highcharts will be merged soon, That will help in daru-view .

-------------------------------------------------