---
layout: post
sciruby_post: true
title: Coding Period Week - 8
week:  23 July 2017 - 29 July 2017
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


#### Mid Term evaluation


##### Meeting on hangout and reviewed each others code

**Athitya reviewed my work on daru-view. Few points he discussed is :**


###### Timeline wise

  * nyaplot : Done
  * highcharts : Done
  * googlecharts : Done
  * datatables : Done
  * matplotlib: Yet to be done
  * chartkick : Not to be done, highcharts is already implemented

###### Discussed

  * Can dummy rails / sinatra / nanoc apps be shifted to examples/ dir? With some tests for each?
  (Also, maybe git-submodules?)
  * Not using CDN Content (Page 3 of proposal).
    Pro: Offline feature
    Con: Frequent updating to daru-view for assets via rake task
    Drop support for Ruby 2.0? Keyword arguments?

###### Code Quality

  * Good work with adapters architecture
  * Couple of Rubocop disables like PerceivedComplexity & CyclomaticComplexity
  * Couple of unused variables on running rspec
  * Tidying specs with rubocop and rubocop-rspec
  * Few minor code style enhancements possible
    case..when (Unnecessary class comparision with is_a?)

    1. lib/daru/view/adapters/googlecharts.rb L107 - L126, L135 - L140, L147 - L158
    2. lib/daru/view/adapters/highcharts.rb L93 - L105
    3. lib/daru/view/adapters/nyaplot.rb L43 - L50
  * Can be DRY-ied (maybe Inheritence?)
  * Update to new YARD doc standards?
  * Usability perspective
  * Download as SVG feature?
  * Better documentation with links to respective JS lib, in README? Because,
    whole usage of daru-view depends on the options that can be passed.
    Monkey-patch into Daru::DataFrame / Daru::Vector for use like df.plot(opts)

-------------------------------------------------


**Few things I reviewed on arrayfire-rb @prasunanand **

* Installation is fine and easy. Just need to install OpenCL and arrayfire. Then we can clone the repo and do according to the readme.

* Works according to the timeline is fine. I see till LAPACK functionalities .ArrayFire- JRuby is yet to be implemented. After that ArrayFire JAVA APIs will be implemented like C++ APIs.

* I tried examples from the test/**.rb files. It works fine. Exceptiosn and proper error msg on wrong arguments is in todo.


-------------------------------------------------
