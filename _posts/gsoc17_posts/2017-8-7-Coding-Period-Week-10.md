---
layout: post
sciruby_post: true
title: Coding Period Week - 10
week:  6 August 2017 - 12 August 2017
posted_on: 22 August 2017
type: post
categories: gsoc2017_post
permalink: /blog/GSoC-2017/:title
tags:
  - Open Source
  - GSoC
  - SciRuby
  - Daru
---


##### 28,29 July 2017 Report :

- Adding more examples for google charts and fixing/adding features .

New examples link: [http://nbviewer.jupyter.org/github/shekharrajak/daru-view/tree/examples/spec/dummy_iruby/](http://nbviewer.jupyter.org/github/shekharrajak/daru-view/tree/examples/spec/dummy_iruby/)

- Improving the documentation. I found that nanoc web application can generate the html code. So it is easy to see the generated site (Some css only works in localhost) : [https://shekharrajak.github.io/daru-view/spec/dummy_nanoc/output/](https://shekharrajak.github.io/daru-view/spec/dummy_nanoc/output/)

- Download button for highcharts is working now. Fixed it here :
[https://github.com/Shekharrajak/daru-view/pull/42](https://github.com/Shekharrajak/daru-view/pull/42)


-------------------------------------------------

##### 30, 31 July 2017 Report :

- Added more examples and use cases of google charts, table and highcharts : Jupyter Notebook Viewer

- Created one rails repo to solve some real world data visualisation problem using daru-io and daru-view : [https://github.com/Shekharrajak/daru_examples_io_view_rails](https://github.com/Shekharrajak/daru_examples_io_view_rails)

We are trying to take data as json from this link [https://api.github.com/orgs/Sciruby/repos](https://api.github.com/orgs/Sciruby/repos)
 and  trying to analyse. The dataframe will be : [http://nbviewer.jupyter.org/github/athityakumar/daru-io/blob/iruby-examples/iruby/json_importer.ipynb](http://nbviewer.jupyter.org/github/athityakumar/daru-io/blob/iruby-examples/iruby/json_importer.ipynb)

- Fixed few bugs in daru-view and trying to make coverage report better.



-------------------------------------------------

##### 1, 2 August 2017 Report :

- Adding examples in Rails app using daru-io and daru-view : [https://github.com/Shekharrajak/daru_examples_io_view_rails](https://github.com/Shekharrajak/daru_examples_io_view_rails)

We are using various json data from the url : [https://api.github.com/orgs/Sciruby/](https://api.github.com/orgs/Sciruby/)repos about the sciruby org in github.

One can see the working here : [https://github.com/Shekharrajak/daru_examples_io_view_rails/pull/4#issuecomment-319760525](https://github.com/Shekharrajak/daru_examples_io_view_rails/pull/4#issuecomment-319760525)

I want to host this small rails app for free. I tried few sites but I got some error or failed to setup. If anyone knows the good tool to host the rails app for free then let me know.

- I see an error while requiring the data_tables : [https://github.com/Shekharrajak/daru_examples_io_view_rails/issues/3](https://github.com/Shekharrajak/daru_examples_io_view_rails/issues/3) but I see that in daru nyaplot and other libraries is added as add_development_dependency (not the add_runtime_dependency )
I think I need something in daru/view/view.rb

-------------------------------------------------

##### 3, 4 Aug 2017 Report :

- Working on a demo rails app to show the features of daru-view and daru-io. Trying to get more data from the github/sciryby api.

I have found some good links, that can be helpful for analysing the sciruby github :

1. [https://api.github.com/repos/SciRuby/daru/contributors](https://api.github.com/repos/SciRuby/daru/contributors)
2. [https://api.github.com/repos/SciRuby/daru](https://api.github.com/repos/SciRuby/daru)

and many other links : [https://developer.github.com/v3/repos/](https://developer.github.com/v3/repos/)

- The rails app shows some error in browser when we do `bundle exec rails s` . I opened a issue to discuss about it (problem seems on google_visualr) : [https://github.com/winston/google_visualr/issues/117](https://github.com/winston/google_visualr/issues/117)

- daru-view/highcharts can work offline. (Nyaplot and googlecharts have some online dependencies). To update the JS files of the daru-view I thought about to defining a command : [https://github.com/Shekharrajak/daru-view/issues/47](https://github.com/Shekharrajak/daru-view/issues/47)

-------------------------------------------------
