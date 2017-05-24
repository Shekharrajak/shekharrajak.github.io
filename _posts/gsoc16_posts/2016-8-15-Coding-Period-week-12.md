---
layout: post
sympy_post: true
title: Coding Period Week 12
week: 8 August 2016 -  15 August 2016
posted_on: 15 August 2016
type: post
categories: gsoc2016_post
permalink: /blog/GSoC-2016/:title
tags:
  - Open Source
  - GSoC
  - SymPy
---

--------------------------------------------------------------------------------

**nonlinsolve continue:**

* PR : [#11111](https://github.com/sympy/sympy/pull/11111)

* few things that should be improved in `nonlinsolve` :

      - If system of equation contains trigonometric functions, `nonlinsolve`
      sometime fails because `solve_trig` of `solveset` is not much better and
      `nonlinsolve` have to identify what is the Intersection soln when we have
      `2*n*pi + pi/2` and `n*pi + pi/2`(means something similar cases).Right now it is returning
      one of them.

      - `substitution` function which solves the system of equation using substitution method.
      There should be better method to handle `imageset` (Complex solution).

      - Code quality of `substitution` should be improved.

--------------------------------------------------------------------------------


**Continue Simplified Trig soln**

* PR [#11188](https://github.com/sympy/sympy/pull/11188)

* Imageset/union is generalized and now it handle basically these three cases:

```
# img1 = ImageSet(Lambda(n, a*n + b), S.Integers)
# img2 = ImageSet(Lambda(n, c*n + d), S.Integers)
In [1]: img1 = ImageSet(Lambda(n, 4*n + 4), S.Integers)

In [2]: img2 = ImageSet(Lambda(n, 4*n), S.Integers)
# when a == c and (b - d == a) then ans is img2.
In [3]: Union(img1, img2)
Out[3]: {4⋅n | n ∊ ℤ}

# -------------------------------------------------------------

In [4]: img1 = ImageSet(Lambda(n, 4*n + 2), S.Integers)
# when a == c and (b - d) == a/2, means value is  a/2 * n
In [5]: Union(img1, img2)
Out[5]: {2⋅n | n ∊ ℤ}

# -------------------------------------------------------------

# 5*n + 5/4 ==> 5*n + 1 + 1/4
# 5*n + 1 + 1/4 is in n + 1/4
# check using img1.superset(img2) == true so img1 in ans
img1 = ImageSet(Lambda(n, n + S(1)/4 ), S.Integers)
img2 = ImageSet(Lambda(n, 5*n + S(5)/4 ), S.Integers)

In [4]: Union(img1, img2)
Out[4]: {n + 1/4 | n ∊ ℤ}

# -------------------------------------------------------------

# img1.issuperset(img2) is false so no change
img1 = ImageSet(Lambda(n, 2*n + S(1)/4 ), S.Integers)
img2 = ImageSet(Lambda(n, 5*n +S(5)/4), S.Integers)
In [5]: Union(img1, img2)
Out[5]: {2⋅n + 1/4 | n ∊ ℤ} ∪ {5⋅n + 5/4 | n ∊ ℤ}

```


--------------------------------------------------------------------------------

**Meanwhile :**

* I found some more cases where `factor_list` fails and opened a PR : https://github.com/sympy/sympy/issues/11528


--------------------------------------------------------------------------------

***continue..***
