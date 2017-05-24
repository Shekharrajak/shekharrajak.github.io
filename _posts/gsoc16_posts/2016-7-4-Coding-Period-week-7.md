---
layout: post
sympy_post: true
title: Coding Period Week 7
week: 3 July 2016 -  9 July 2016
posted_on: 4 July 2016
type: post
categories: gsoc2016_post
permalink: /blog/GSoC-2016/:title
tags:
  - Open Source
  - GSoC
  - SymPy
---

**ImageSet.put_values() :**

PR [#11343](https://github.com/sympy/sympy/pull/11343)

* After the discussion Harsh told that it is better to use like `imageset.lamda(values_for_lambda_var)` directly, also don't make lambda variables public , it should be local and before doing `imageset.lamda(values_for_lambda_var)` this one need to check whether values are in ` base_set` or not.

* You can see the previous code here : [gist](https://gist.github.com/Shekharrajak/d70a36c95eefaca5c684497e039c5632)

* I updated the docs stating how to put certain values in ImageSet lambda variables.(reverted my changes and edited the ImageSet docs in the PR.)

**Continue nonlinsolve :**

PR [#11111](https://github.com/sympy/sympy/pull/11111)

* How Intersections and Complements are handled :

see these examples:

```
In [ ]: intr = Intersection(FiniteSet(x), Interval(1,10))

In [ ]: comp = Complement(FiniteSet(x), Interval(1,10))

In [ ]: intr
Out[ ]: [1, 10] ∩ {x}

In [ ]: comp
Out[ ]: {x} \ [1, 10]

In [ ]: type( Intersection(comp, Interval(1,11)))
Out[ ]: sympy.sets.sets.Complement

In [ ]: type(Complement(intr, Interval(1,2)))
Out[ ]: sympy.sets.sets.Complement


```

So first handling the Complements and then intersection will be checked in solveset soln.

* `nonlinsolve` can handle simple trigonometric system of equations but when complex equations
is used then it will return `ConditionSet` since `solveset` trig solver is not smart enough right now.

* Trying to break the code into the functions to make the code better.

--------------------------------------------------------------------------------

**Continue Simplified Trig soln**

PR [#11188](https://github.com/sympy/sympy/pull/11188)

* I was getting problem in ImageSet union when you run test. Sometimes it pass all the cases but not always.
I found the problem (most probably because order of args in union.reduce is not always same for all the python version
I am using FiniteSet so I hope it is good way to handle this.) Now it passes all the checks all time.


--------------------------------------------------------------------------------

**Meanwhile :**

* I found that `Mod` is not defined for complex numbers. e.g.

```
In [1]: g = Mod(-log(3), 2*I*pi)

In [2]: g
Out[2]: Mod(-log(3), 2⋅ⅈ⋅π)

In [3]: simplify(g)
Out[3]: Mod(-log(3), 2⋅ⅈ⋅π)

In [4]: simplify(g)
Out[4]: Mod(-log(3), 2⋅ⅈ⋅π)

In [5]: g2 = Mod(-log(3), 2*pi)

In [6]: simplify(g2)
Out[6]: -log(3) + 2⋅π

In [7]: simplify(Mod(I,I))
Out[7]: 0

In [8]: simplify(Mod(2*I,I))
Out[8]: 0

In [9]: simplify(Mod(2*I,3*I))
Out[9]: 5⋅ⅈ

In [10]: simplify(Mod(2*I,1+3*I))
Out[10]: Mod(2⋅ⅈ, 1 + 3⋅ⅈ)

```
Need to implement `Mod` for complex number as well. There is concept og Gaussian Integers

Some resources I found is this :
[link1](http://math.stackexchange.com/questions/274694/modulo-complex-number),
[link2](http://www.freemathhelp.com/forum/threads/76383-Modulo-of-complex-numbers),
[link3](https://en.wikipedia.org/wiki/Gaussian_integer)
[link4](http://fermatslasttheorem.blogspot.in/2005/06/division-algorithm-for-gaussian.html)

* One can see the issue [11391](https://github.com/sympy/sympy/issues/11391) for detail discussion.

* Tried to fix the bug of `is_zero_dimensional` in this PR [#11371](https://github.com/sympy/sympy/pull/11371).

--------------------------------------------------------------------------------
***continue..***
