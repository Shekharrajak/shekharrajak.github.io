---
layout: post
title: Coding Period Week 11
week: 1 August 2016 -  7 August 2016
posted_on: 7 August 2016
type: post
---

--------------------------------------------------------------------------------

**eliminate() continue:**

* PR : [#11485](https://github.com/sympy/sympy/pull/11485)

* Regarding issue [#2720](https://github.com/sympy/sympy/issues/2720), It is something similar to `eliminate` present in
[wolfram](http://reference.wolfram.com/mathematica/ref/Eliminate.html).

* Right now it is working for real domain and not considering ImageSet, Intersection. Complement. If it find ImageSet, Intersection. Complement
for the symbol to be eliminated, then just raises `NotImaplementedError`(in near future it can be implemented).

* It can take `N` nummber of equations and `M` number of `symbols` to be eliminated. It returns `FiniteSet` of equations which doesn't contains
these `symbols`.

--------------------------------------------------------------------------------

**Continue - Diophantine in Solveset :**

PR [11234](https://github.com/sympy/sympy/pull/11234)

* In [commit](https://github.com/sympy/sympy/pull/11234/commits/6bd9689d37647d6c28111097c433accc2127262e) : returning
`ConditionSet` when it `diophantine` doesn't the diophantine equation type and not able to solve.

--------------------------------------------------------------------------------

**Meanwhile :**

* Some analysis about `Abs` solver :

```

In [1]: solveset(Abs(x) - 1,  x)
ValueError:
Absolute values cannot be inverted in the complex domain.

In [2]: solveset(Abs(x) - (1 + I), x)
ValueError:
Absolute values cannot be inverted in the complex domain.

In [3]: solveset(Abs(x) - y , x)
ValueError:

```
Absolute values cannot be inverted in the complex domain.
- In 1st case (for complex domain) ans should be [http://www.wolframalpha.com/input/?i=Abs(x)+-+(1+)+%3D0+for+x](http://www.wolframalpha.com/input/?i=Abs(x)+-+(1+)+%3D0+for+x)

- In 2nd case EmptySet.
and in 3rd case (general solution when domain=S.Complexes) soln should be [http://www.wolframalpha.com/input/?i=Abs(x)+-+y+%3D0+for+x](http://www.wolframalpha.com/input/?i=Abs(x)+-+y+%3D0+for+x)

- In general( 3rd case) it should print
ConditionSet(x, -Abs(re(y)) <= re(x) and re(x) <= Abs(re(y)) and re(y)>0, Eq(im(y), 0) , S.Complexes).


--------------------------------------------------------------------------------

***continue..***

--------------------------------------------------------------------------------
