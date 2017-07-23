---
layout: post
sciruby_post: true
title: Coding Period Week - 4
week:  1 July 2017 - 6 July 2017
posted_on: 22 July 2017
type: post
categories: gsoc2017_post
permalink: /blog/GSoC-2017/:title
tags:
  - Open Source
  - GSoC
  - SciRuby
  - Daru
---


#### Google charts tool continue


##### 2, 3 July 2017 Report :

- Analysing google charts in the website  and found some bugs in google_visualr. Trying to fix them in daru-view. Trying more examples from the site.

- Few examples added in [this notebook](http://nbviewer.jupyter.org/github/shekharrajak/daru-view/blob/google_chart/spec/dummy_iruby/Google%20Charts%20%7C%20Basics.ipynb)

- rake file added for the google chart to update the JS files using `rake googlecharts:update` command.

- Adding specs.

-------------------------------------------------

##### 4, 5 July 2017 Report :

1.  I read articles and watched few videos on DataTable. Discussing about it in [this forum](https://datatables.net/forums/discussion/comment/113864#Comment_113864)

2.  These 2 links shows, how DataTable can handle millions of rows, very fast :

- [server-side_processing](https://datatables.net/extensions/scroller/examples/initialisation/server-side_processing.html)

- [large_js_source](https://datatables.net/extensions/scroller/examples/initialisation/large_js_source.html)

some server side process, that can be useful to load data into pieces:

- [https://www.driftingruby.com/episodes/datatables](https://www.driftingruby.com/episodes/datatables)


-------------------------------------------------

##### 6, 7 July 2017 Report :

- Added google charts examples in spec/dummy_rails , dummy_sinatra, dummy_nanoc web application.

- Working on DataTables for daru-view. [Discussion link](https://datatables.net/forums/discussion/comment/114005#Comment_114005)

If I am correct then there is no Ruby gem right now for DataTables, that can generate the html, javascript code and display the tables. I am thinking to create a gem that can generate simple javascript for the DataTables.

- Adding specs and trying to make coverage report better.


-------------------------------------------------

