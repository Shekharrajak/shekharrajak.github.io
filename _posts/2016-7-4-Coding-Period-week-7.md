---
layout: post
title: Coding Period Week 6
week: 3 July 2016 -  9 July 2016
posted_on: 4 July 2016
type: post
---

**ImageSet.put_values() :**

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
Out[2]: 1

In [3]: img = ImageSet(Lambda((n, m), n**2 + m) , S.Reals)

In [4]: img.put_values({n: 1, m: 2})
Out[4]: 3

```

* I want to use this in PR [#11188](https://github.com/sympy/sympy/pull/11188)

--------------------------------------------------------------------------------

***continue..***
