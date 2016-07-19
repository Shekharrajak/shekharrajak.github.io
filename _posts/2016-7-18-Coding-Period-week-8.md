---
layout: post
title: Coding Period Week 8
week: 10 July 2016 -  16 July 2016
posted_on: 18 July 2016
type: post
---

--------------------------------------------------------------------------------
**Continue - Diophantine in Solveset :**

PR [11234](https://github.com/sympy/sympy/pull/11234)

* For general Pythagorean diop_type (Diophantine eq type), it seems diophantine always returns parameterized solution so I did required changes in the PR. [commit](https://github.com/sympy/sympy/pull/11334/commits/6af46fc35db3a74dfda78b6d8e2a0f7d4ec65afe)

* You can refer this [comment](https://github.com/sympy/sympy/pull/11334#issuecomment-230334645).

--------------------------------------------------------------------------------

**Continue Simplified Trig soln**

PR [#11188](https://github.com/sympy/sympy/pull/11188)

* After some changes the PR is ready for review.


--------------------------------------------------------------------------------

**Continue nonlinsolve :**

PR [#11111](https://github.com/sympy/sympy/pull/11111)

* Added some XFAIL test-cases of system of Trigonometric equations, since `solveset` trig solver (`solve_trig`) is not smart enough. Sometimes it return soln in ConditionSet (which can be solved using `_invert` or inverse Trigonometric functions). So `solveset` returns `ConditionSet` that means `substitution` is not getting soln and at the end returns `ConditionSet`.

* It is better to replace trigonometric functions or other `Function` with symbols (e.g. `sin(x)` --> `u`, `sin(y)`--> `v`, `f(x)`--> `f_x`, `g(x)` --> `g_x`) and then solve for the symbols. After getting solution
from `nonlinsolve` user can invert or do `solveset`(e.g. solveset(Eq(sin(x), soln_u), x, domain) to get value of `x`).

--------------------------------------------------------------------------------

**Meanwhile :**

* We already know that solveset need improved `invert_real` , `invert_complex` and `Imageset` Intersections.

* previous work is in this PR [10971](https://github.com/sympy/sympy/pull/10971). Trying to improve them.

Some cases is here :

```
# In 2, 4, 5 intersection is not needed.

In [1]: img = ImageSet(Lambda(n, x/n), S.Complexes)

In [2]: Intersection(img, S.Complexes)
Out[2]:
    ⎧x        ⎫
ℂ ∩ ⎨─ | n ∊ ℂ⎬
    ⎩n        ⎭

In [3]: img = ImageSet(Lambda(n, x/n), S.Integers)

In [4]: Intersection(img, S.Complexes)
Out[4]:
⎧x        ⎫    
⎨─ | n ∊ ℤ⎬ ∩ ℂ
⎩n        ⎭    

In [5]: Intersection(ImageSet(Lambda(n, 2*n*I*pi), S.Integers), S.Complexes)
Out[5]: {2⋅ⅈ⋅π⋅n | n ∊ ℤ} ∩ ℂ

# ImageSet Intersection is not implemented when inverter returns 2 values.
# here ans should be {0, 1}
In [6]: img1 = ImageSet(Lambda(n, n**2), S.Integers)

In [7]: Intersection(img1, Interval(0,2))
Out[7]:
         ⎧ 2        ⎫
[0, 2] ∩ ⎨n  | n ∊ ℤ⎬
         ⎩          ⎭

```

--------------------------------------------------------------------------------

***continue..***
