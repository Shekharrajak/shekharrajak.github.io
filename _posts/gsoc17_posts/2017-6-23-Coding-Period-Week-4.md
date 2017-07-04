---
layout: post
sciruby_post: true
title: Coding Period Week - 4
week:  23 June 2017 - 30 June 2017
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


#### Google charts tool


##### 23, 24 June 2017 report :

- Added specs (it really takes time) and fixed bugs.
- More examples added in iruby notebook. Daru Visualisation examples added.
- Working on nanoc app examples.
- Adding Google chart tool using google_visular gem.

-------------------------------------------------

##### 26, 27 June Report :

 -  Google Chart : Mostly tried examples and designing the methods similar to other libraries.
 - I found that Google Chart table package is able to do pagination and some custom styling (CSS), I am working on it.

Adding google chart in this PR:[ https://github.com/Shekharrajak/daru-view/pull/32](https://github.com/Shekharrajak/daru-view/pull/32)


Discussed it in this :

- [https://github.com/winston/google_visualr/issues/112](https://github.com/winston/google_visualr/issues/112)

- [https://github.com/winston/google_visualr/issues/109](https://github.com/winston/google_visualr/issues/109)

- A example I added in wiki : [https://github.com/Shekharrajak/daru-view/wiki/Google-charts-:-Creating-data-table-with-pagination-feature](https://github.com/Shekharrajak/daru-view/wiki/Google-charts-:-Creating-data-table-with-pagination-feature)


- I am trying to run mtplotlib.rb in iruby notebook. I find some difficulty in matplotlib.rb iruby notebook.

-------------------------------------------------

##### 28 June 2017 Report :

- Working on adapter google chart tool. Google chart tool uses DataTable , to take input the data. So I am thinking to use this Google chart Table , as one of the library for generating/drawing data table.

- Designing the `Table` class similarly to `Plot` class to generating the table for the webpage and iruby notebook.  There was some problem in drawing the table. I fixed it in my own forked repo of google_visualr gem .

- This `Table` class will be able to generate html table (for both iruby notebook and webpage) , taking input as DataFrame/Vector/Array . It will be usable in the plotting library to get the data.

-------------------------------------------------

##### 29, 30 June 2017 :

- Mostly worked on Google Chart - DataTable. Defined `Table` class and after setting adapter as googlecharts  and passing the DataFrame/Vector, it is able to display table.

Examples : [http://nbviewer.jupyter.org/github/shekharrajak/daru-view/blob/google_chart/spec/dummy_iruby/GoolgeChart%20%7C%20Datatables.ipynb](http://nbviewer.jupyter.org/github/shekharrajak/daru-view/blob/google_chart/spec/dummy_iruby/GoolgeChart%20%7C%20Datatables.ipynb)

- This table can be directly used to plot charts. Google chart need data in google DataTable, to plot the charts.

- There are pagination features available, that can work in iruby notebook as well as web application.

- I write some internal concepts in wiki page : [https://github.com/Shekharrajak/daru-view/wiki](https://github.com/Shekharrajak/daru-view/wiki)

-------------------------------------------------
