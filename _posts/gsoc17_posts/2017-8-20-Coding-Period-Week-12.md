---
layout: post
sciruby_post: true
title: Coding Period Week - 12
week:  20 August 2017 - 26 August 2017
posted_on: 27 August 2017
type: post
categories: gsoc2017_post
permalink: /blog/GSoC-2017/:title
tags:
  - Open Source
  - GSoC
  - SciRuby
  - Daru
---


##### Report :

- Wrote few things about daru-view in wiki page : https://github.com/Shekharrajak/daru-view/wiki

- Noting down and tried to solve the issues/comments in daru-view and sample rails app.

Because of new joining to a company, attending freshers program, long training program  and shifting twice (1st in hotel for around 14 days and then to a rent room PG ) have disturbed my daily routine.


-------------------------------------------------

##### 23 aug 2017 report :

- Worked on ideas proposed in this PR of the sample rails app :[ https://github.com/Shekharrajak/daru_examples_io_view_rails/pull/12]( https://github.com/Shekharrajak/daru_examples_io_view_rails/pull/12)

This comment state the idea of daru_chart and daru_table in rails app. I have implemented the same in this PR : [https://github.com/Shekharrajak/daru-view/pull/55](https://github.com/Shekharrajak/daru-view/pull/55)

- And using the daru_chart and daru_table in sample rails app : [https://github.com/Shekharrajak/daru_examples_io_view_rails/pull/13](https://github.com/Shekharrajak/daru_examples_io_view_rails/pull/13)

- So in rails app we can do this :

for table :

````
<%= daru_table(data, options) %>
```

for chart :

```
<%= daru_table(data, options) %>
```

Parameters data and options can be same as `Daru::View::Plot` and `Daru::View::Table` .

-------------------------------------------------
