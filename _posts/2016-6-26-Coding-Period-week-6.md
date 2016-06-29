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

--------------------------------------------------------------------------------
**Continue - Diophantine in Solveset :**

PR [11234](https://github.com/sympy/sympy/pull/11234)

* Some points we discussed :

1. `Solveset` should return all the solution, so we need to check for which kind of eq. `diophantine` returns all
the solution. We can get the equation type using `classify_diop` defined in `diophantine.py`.

2. If there is the case where `diophantine` doesn't return all the solutions then just return `ConditionSet` or try to
make all solution (e.g. if just need to permute sign in values then use `permute_signs`).

* After reading the [diophantine Documentation](http://docs.sympy.org/dev/modules/solvers/diophantine.html) and `diophantine` doctests and examples, I found that :

1.



**continue...**
