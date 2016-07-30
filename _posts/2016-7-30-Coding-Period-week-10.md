---
layout: post
title: Coding Period Week 10
week: 24 July 2016 -  30 July 2016
posted_on: 30 July 2016
type: post
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

**_continue_**
