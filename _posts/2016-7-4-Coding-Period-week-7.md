---
layout: post
title: Coding Period Week 7
week: 3 July 2016 -  9 July 2016
posted_on: 4 July 2016
type: post
---

<!-- **ImageSet.put_values() :**

PR [#11343](https://github.com/sympy/sympy/pull/11343)

* We need `put_values` attribute, because we can't do `subs` to put finite values in `ImageSet`.

```
In [1]: imgset = ImageSet(Lambda((n, m), n**2), S.Reals)

In [2]: imgset.subs(n,1)
---------------------------------------------------------------------------
TypeError: variable is not a symbol: 1

In [3]: imgset.subs(n,x)
Out[3]:
⎧ 2           ⎫
⎨x  | x, m ∊ ℝ⎬
⎩             ⎭

```

Using this PR :

```
In [1]: img = ImageSet(Lambda((n, m), n**2) , S.Reals)

In [2]: img.put_values({n: 1, m: 2})
Out[2]: {1}

In [3]: img = ImageSet(Lambda((n, m), n**2 + m) , S.Reals)

In [4]: img.put_values({n: 1, m: 2})
Out[4]: {3}

```

* I want to use this in PR [#11188](https://github.com/sympy/sympy/pull/11188) and
[#11257](https://github.com/sympy/sympy/pull/11257) -->

**nonlinsolve :**

PR [#11111]((https://github.com/sympy/sympy/pull/11111)

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

--------------------------------------------------------------------------------


***continue..***
