---
layout: post
sciruby_post: true
title: Coding Period Week - 7
week:  16 July 2017 - 22 July 2017
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


#### Google charts tool continue &  DataTables


##### 17, 18 July 2017 Report :

- After this PR [https://github.com/SciRuby/daru/pull/366]( https://github.com/SciRuby/daru/pull/366) I have added example for highcharts examples (iruby notebook and rails application) here : [https://github.com/Shekharrajak/daru-view/pull/38](https://github.com/Shekharrajak/daru-view/pull/38)

Examples shows, how we can use html table as data source for plotting the chart.

- I have added few more examples in data_tables : [https://github.com/Shekharrajak/datatables.rb/pull/6/files](https://github.com/Shekharrajak/data_tables/pull/6/files)

These examples shows how user can use the html table generated from the daru dataframe and vector and add the datatables class and styling to transform it into DataTables table form with pagination and search features .


-------------------------------------------------

##### 19, 20 July 2017 Report :

- Tested DataTables with Array of arrays data and data in html table form in rails application : [https://github.com/Shekharrajak/datatables.rb/pull/6](https://github.com/Shekharrajak/data_tables/pull/6)

It is working fine in rails application, but I am not able to see the table in iruby notebook. Actually it is not using the js that is loaded in notebook (when I run `DataTable.init_iruby`).

- rake file is added in datatables.rb to update the js files automatically by running rake command. There are many more js and css file to be added for more features .

- Initial code have added in daru-view for DataTables : [https://github.com/Shekharrajak/daru-view/pull/39](https://github.com/Shekharrajak/daru-view/pull/39)


-------------------------------------------------

##### 21, 22 July 2017 Report :

- Most of the works was around [data_tables](https://github.com/Shekharrajak/data_tables) . Now using this gem we can get datatables from the data array and html code of the table.

Refer : [https://github.com/Shekharrajak/data_tables/pull/6](https://github.com/Shekharrajak/data_tables/pull/6)

- I still didn't understand why it is not working in IRuby notebook. I have loaded the dependent js  files (don't know how to load css files in iruby notebook). In out put cell I can see the script and table code. But the JS code is not invoked, so it is just working as normal html table code.

- Since it is working fine in web application (Rails) [You can check the example in the spec/dummy_rails ] .

- I have added data_tables in daru-view in this PR:[ https://github.com/Shekharrajak/daru-view/pull/39]( https://github.com/Shekharrajak/daru-view/pull/39
)

Also I have added examples in spec/dummy_rails application. Example shows how we can use  Daru DataFrame and Vector as the  data source for the data_tables. Also it will work when data is given as array.

- There are many options that can be used in data_tables . [Examples link](https://datatables.net/examples/index)

- Default options are pagination, search, show entries.

- Using data_tables we can load the large dataset piece by piece (more scroll more data will be loaded). I have discussed about it [here](https://datatables.net/forums/discussion/43379).

Using server side processing, data can be loaded from the url or some file and ajax method can be used to load data piece by piece. More work has to be done, in this area.


-------------------------------------------------
