---
layout: post
title: Coding Period Week 6
week: 26 June 2016 -  2 May 2016
posted_on: 21 June 2016
type: post
---

**Continue nonlinsolve :**

PR [#11111](https://github.com/sympy/sympy/pull/11111)

* Removed the dependency of old solvers `_invert`. It was basically helpful for removing `sqrt` or Rational power.
Now using `unrad` and little changes in `substitution` function can handle the system havning `sqrt` or `cube root`.


**continue...**
