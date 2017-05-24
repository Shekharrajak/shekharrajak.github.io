---
layout: post
sympy_post: true
title: Coding Period Week 10
week: 24 July 2016 -  30 July 2016
posted_on: 30 July 2016
type: post
categories: gsoc2016_post
permalink: /blog/GSoC-2016/:title
tags:
  - Open Source
  - GSoC
  - SymPy
---

--------------------------------------------------------------------------------

**eliminate() continue:**

* issue [#2720](https://github.com/sympy/sympy/issues/2720) : We need some kind of eliminate function, like [http://reference.wolfram.com/mathematica/ref/Eliminate.html](http://reference.wolfram.com/mathematica/ref/Eliminate.html). See also [http://stackoverflow.com/q/20826969/161801 ](http://stackoverflow.com/q/20826969/161801)

* I am trying to use `subs` and `_invert` to get answer. May be one can use `replace`, `xreplace`, `match` to eliminate some kind of same sub expression.

* There can be ans in `Imageset`, `Finiteset`, `Complement`, `Intersection` when we use `_invert`. So there should be a technique to handle it.

* Still need some good idea and technique. WIP.

--------------------------------------------------------------------------------

**Output of solveset should be of one type:**

* Amit discussed about it. Solution we see in `solveset` should be in one type of set. Right now we may have solution in `Imageset`, `Finiteset`, `Complement`, `Intersection` or `ConditionSet`. So there would be problem for user to handle these many solution type.

* I think there should be something that separate `Complements`, `Intersections`,`ConditionSet` and main solution in `Finiteset`.

* E.g. if solveset solution is `Intersection(Complement(FiniteSet(x), {y}), {z})` then
soln : `FiniteSet(x)`, `x != {y}`, `{x} intersect {z}`.

--------------------------------------------------------------------------------

**Continue Simplified Trig soln**

PR [#11188](https://github.com/sympy/sympy/pull/11188)

* According to the [Harsh comments/review](https://github.com/sympy/sympy/pull/11188#issuecomment-234789616) I modified the PR. Now it seems it is
returning more simplified solution( [one case is here](https://github.com/sympy/sympy/pull/11188/commits/beaac312f03819bd7221887eb2b4cbe5d49bed5e#diff-85baa04bbf4e1dfd9128782738e45424R1141)) .

* To understand the changes I did in the `_solve_trig` method, one should check [this gist](https://gist.github.com/Shekharrajak/17fdcd2320f572fc9fc8674823137e20)

* To see the advantage of imageset union, One good example is in [this gist](https://gist.github.com/Shekharrajak/a5efc840d9a7d3062289f2d9c5f20b16)

--------------------------------------------------------------------------------

**_continue_**
