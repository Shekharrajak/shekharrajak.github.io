---
layout: post
sciruby_post: true
title: Coding Period Week - 2
week:  7 June 2017 - 15 June 2017
posted_on: 15 June 2017
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


##### 6 June 2017 Report:

1. lazy_high_charts for IRuby notebook : The PR : [https://github.com/michelson/lazy_high_charts/pull/236](https://github.com/michelson/lazy_high_charts/pull/236) was almost completed but we found one problem in loading the initial js files when we run `require lazy_high_charts`. See this comment .

Examples I tried is here : [http://nbviewer.jupyter.org/github/Shekharrajak/lazy_high_charts/blob/iruby_setup/spec/dummy_iruby/lazy_high_charts_basics.ipynb](http://nbviewer.jupyter.org/github/Shekharrajak/lazy_high_charts/blob/iruby_setup/spec/dummy_iruby/lazy_high_charts_basics.ipynb)

We can see that above link's page source load the entire JS file when `require lazy_high_charts` is run. But still some 3d charts doesn't display. Also when we run the `.show` output cell comes empty. But when we save the notebook file in html or other format we can see the charts. (I followed the Nyaplot way of init_iruby notebook ).

I am doing similar things for google charts. Discussed some point here : [https://github.com/winston/google_visualr/issues/109](https://github.com/winston/google_visualr/issues/109)


2. Nyaplot :

Updated the PR : [https://github.com/SciRuby/daru/pull/350](https://github.com/SciRuby/daru/pull/350) . There is some problem in generating the div part of the chart from the Nyaplot side I am looking into it. Loading the inital JS file and body part of the charts working fine.

-------------------------------------------------

##### 7 June 2017 Report :

1. Tried to fix the bug in [lazy_high_charts iruby notebook PR](https://github.com/michelson/lazy_high_charts/pull/236) . I think because of large JS code IRuby notebook taking time, so when we save the html page it shows the chart correctly. I am trying to load minimum required JS for the particular chart.  I will try to use the code of the PR in daru-view to display chart in iruby.

2. Along with this I tried to run google chart gem google_visualr in IRuby notebook and [opened a PR](https://github.com/winston/google_visualr/pull/110) . In this PR it is working fine for most of the charts except 1 or 2 charts type. I am trying to fix them.

3. Adding testcases.

-------------------------------------------------

##### 8, 9 June 2017 Report :

1. Highcharts JS files loaded into the daru-view and using the downloaded files for plotting.  User can load the JS files in Iruby notebook or add the JS in the head tag of the application. `div` part of the chart is generated and is usable in the body part. Check the new commit

2. I am struggling with 2 issues : [https://github.com/Shekharrajak/daru-view/issues/5](https://github.com/Shekharrajak/daru-view/issues/5) and [https://github.com/Shekharrajak/daru-view/issues/6](https://github.com/Shekharrajak/daru-view/issues/6) . There is minor problems but still finding them.

--
Next goals :

- add Sinatra and Nanoc web application in specs like dummy_rails web application and add more examples in it.
- More specs
- Add all examples in spec/dummy_iruby
- Try to fix issues.

-------------------------------------------------

##### 10 june 2017 :

1. Found the bug related to  [https://github.com/Shekharrajak/daru-view/issues/6](https://github.com/Shekharrajak/daru-view/issues/6) . The bug is related to this comment .  Using the new defined method in the daru-view for generating div part, will display the charts properly in iruby notebook.

2. Worked on google chart gem for iruby, related to this PR : [https://github.com/winston/google_visualr/pull/110](https://github.com/winston/google_visualr/pull/110)

-------------------------------------------------

##### 11 june 2017 :

- I have added few line to automate the loading of JS files in iruby notebook when plotting_library is set , [in this commit](https://github.com/Shekharrajak/daru-view/pull/9/commits/9e94d9184e07d0b0029d54c672e429c9e0e12f3d).

When user run this line in notebook `Daru::View.plotting_library = :highcharts` then JS files will be loaded automatically.

An example : [http://nbviewer.jupyter.org/github/Shekharrajak/daru-view/blob/nyaplot_highcharts/spec/dummy_iruby/Pie%20Chart%20using%20HighCharts2.ipynb](http://nbviewer.jupyter.org/github/Shekharrajak/daru-view/blob/nyaplot_highcharts/spec/dummy_iruby/Pie%20Chart%20using%20HighCharts2.ipynb)

I am working on some method that will take data from DataFrame (data of some particular column for X axis, Y axis, Z axis (Z axis for some charts like bubble charts), and other Options   ), currently it converts the DataFrame to Array of rows and uses the 1st column for X axis and 2nd column as Y Axis.


-------------------------------------------------



##### 12 June 2017 Report ;

- Looking for a good design for the method that will use the Daru Dataframe or Vector directly in the HighCharts to plot the chart.

- Example : In various line charts One vector or Dataframe will be used. Vector means one line graph, DataFrame means each column will be used to plot line in one chart frame. Index values will be used as xAxis categories . Dataframe column name as Line series name.

- Putting the Nyaplot dependent JS files in daru-view to use make it usable in offline mode.


-------------------------------------------------

##### 13 June 2017 Report :

- Working on HighCharts in daru-view : A suitable method that can handle both HighCharts kind of input and daru DataFrame/Vector input.
PR: [https://github.com/Shekharrajak/daru-view/pull/9](https://github.com/Shekharrajak/daru-view/pull/9)

Example : [http://nbviewer.jupyter.org/github/shekharrajak/daru-view/blob/nyaplot_highcharts/spec/dummy_iruby/add_series%20method%20for%20%20adding%20multiple%20charts%20in%20one.ipynb](http://nbviewer.jupyter.org/github/shekharrajak/daru-view/blob/nyaplot_highcharts/spec/dummy_iruby/add_series%20method%20for%20%20adding%20multiple%20charts%20in%20one.ipynb)

-------------------------------------------------

##### 14, 15 June 2017 Report:

1. Added various JS dependencies of Highcharts and Nyaplot in daru-view. (But Nyaplot still needs the internet , internally in js file, I think).

2. Tried various kinds of charts (more than 50) that can be generated using Highcharts in rails App. I will add all the examples in iruby notebook and dummy_rails app in the daru-view.


-------------------------------------------------
