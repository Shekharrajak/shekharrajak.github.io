---
layout: post
scipy_post: true
title: GSoD NumPy & SciPy Application
week:
posted_on: 28 August 2019
categories: gsod2019_post
type: post
permalink: /blog/GSoD-2019/:title
tags:
  - Open Source
  - GSoD
  - SciPy
  - NumPy
  - Google Season of Docs
  - Quansight
  - Documentation
---


#### Getting up for Project

I came across a new program call Google Season of Docs. The origin of this program is basically from the GSoC mentor mailing list. I remember after completion of GSoC 2018 few members pointed out that writing documentation is very necessary along with the maintaing and developing the software.

Past GSoC mentors and students proposed Google to organize a separate program, just of improving the documentation of the Open Source Softwares.

Next year 2019 Google announced the program - [Google Season of Docs](https://opensource.googleblog.com/2019/04/season-of-docs-org-apps.html).

I found very interesting project ideas from various organizations. NumPy and SciPy [project idea](https://github.com/numfocus/gsod/blob/master/2019/NumPy_ideas_list.md) attracted me.

The project is Restructuring and redesigning of the NumPy & SciPy website. I used to read API docs in numpy site which has pretty old UI and bit redundent documentation. I decided to work on it.

#### NumPy

**Abstract of the proposal**

[NumPy](http://www.numpy.org/) is an incredible library to perform mathematical and statistical operations. It works perfectly well for multi-dimensional arrays and matrices multiplication. NumPy version 1.0 was released in 2006 and now it is widely used in mathematical, scientific, engineering, and data science programming.

NumPy API documentation provide good description about the method and example.

But it is still using old Sphinx template and modern days we have better SSG(Static Site Generator) tools. Also there is need of restructuring of pages and making it more useful for users by adding new examples and tutorials.


My main intention is :

● To design and develop better UI for [www.numpy.org](http://www.numpy.org).

● To enhance and modify the contents of [www.numpy.org](http://www.numpy.org): NumPy User Guide, NumPy Benchmarking, F2Py Guide, NumPy Developer Guide, Building and Extending the Documentation, NumPy Reference , About NumPy, Reporting bugs and all other related to Development pages.

● Add contents about when to use NumPy and when to use XND, Dask array Python libraries, which provides similar APIs.

● To preserve the Python API documentation which is generated using Sphinx (current Documentation Processing Tool for Python, which is the best tool, as per my knowledge for Python) and work on better [Sphinx theme](https://github.com/scipy/scipy-sphinx-theme).


**Brief Overview **

Current [www.numpy.org](http://www.numpy.org) page uses Sphinx for generating the docs (using docstring written before the method or class) for Python APIs and also for writing the static pages like:  NumPy User Guide, NumPy Benchmarking, F2Py Guide, NumPy Developer Guide, Building and Extending the Documentation, NumPy Reference , About NumPy pages.

So here we can shift the Static pages into better UI using SSG (Static Site Generator) frameworks.

The main point is, we should have the following features in NumPy Static pages :


1. Markdown based: So that technical writers don't have to worry about installation. They can write simply in .md file. Anyone can click on edit button shown in website (new feature) and contribute (edit/suggest changes for the page in Github) to make it better. This will engage users to add new content or edit content to improve it.

2. Documentation Search:  User should be having search box, so that they can easily and quickly find out relevant contents.

3. Document Versioning: User should be able to switch between the old and new versions easily. They should be able to checkout old version details as well.

4. Localization/Translation:  User may have option to switch between languages. They should be able to read in native language as well.

5. New release note and Blogs:  Website should be updated with new blog posts and news about the current development and roadmap. So kind of blogging should be present in landing page.

6. Fast development:  Most of the SSG (Static Site Generator) frameworks are running in server and changes in file reflects immediately in UI. Also deploy and build process should be easy.

7. In future, if we want to change the framework, we use. Then it should be easy. Most of the frameworks support Markdown writing so just moving the .md files and few changes should be enough.

8. Framework should provide flexibility to extend the features or add new features easily. So framework should have plugin system.


#### Discussions


●  Mostly discussed in mailing thread: numpy-scipy-gsod, titled: ‘Interested to participate Google Season of Docs 2019 - NumPy’.


#### Project link :

[GSoD 2019 - NumPy - High level restructuring and end user focus](https://docs.google.com/document/d/1l6YBZmS_dh2Ox9piGK4qaMgTDOspmOYxxbSdWW7FKrI/edit?usp=sharing)


-------------------------------------------------
