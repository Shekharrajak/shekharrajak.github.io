---
layout: post
title: Coding Period Week 4
week: 12 June 2016 - 18 June 2016
posted_on: 13 June 2016
type: post
---

#### `Solveset` when `domain = S.Integers`

PR [#11234](https://github.com/sympy/sympy/pull/11234)

Right now we may not get our solution in Integer domain but we can use concept of diophantine equations in `solveset`.
When I messaged about this in giiter channel Aaron told about the `diophantine`, already defined in solvers/diophantine.py.
So we can use `diophantine` in `solveset` to get Integer solution.`diophantine` is coded pretty well and works fine.

##### Diophantine Equations

Let P(x, y, ...) is a polynomial with integer coefficients in one or more variables.
A Diophantine equation is an algebraic equation

```
P(x, y, z, ... ) =  0
```

for which integer solutions are sought.

* More about diophantine equation [mathworld.wolfram](http://mathworld.wolfram.com/DiophantineEquation.html)

**Previous work on this :**

PR [#10994](https://github.com/sympy/sympy/pull/10994)

**solveset_univariate_trig_ineq :***

* Problem in current branch:

```
In [ ]: solveset((2*cos(x)+1)/(2*cos(x)-1) > 0, x, S.Reals)
Out[ ]:
(-oo, pi/3) \ ImageSet(Lambda(_n, 2*_n*pi + 5*pi/3), Integers()) U ImageSet(Lambda(_n, 2*_n*pi + pi/3), Integers()) U (2*pi/3, 4*pi/3) \ ImageSet(Lambda(_n, 2*_n*pi + 5*pi/3), Integers()) U ImageSet(Lambda(_n, 2*_n*pi + pi/3), Integers())

```

solution expected is :

`(1/3)*(3*pi*n - pi) < x < (1/3)*(3*pi*n +pi), n element in Z`

I am working on this right now.

**Meanwhile**

* Opened an issue [#11236](https://github.com/sympy/sympy/issues/11236).

* PR [#11239](https://github.com/sympy/sympy/pull/11239) for the issue

* I found that right now `diophantine` can't handle these types of equations :

```
In [ ]: diophantine((x+y)**2 - x**3 + y**3)
---------------------------------------------------------------------------
NotImplementedError: No solver has been written for cubic_thue.

```

**continue..**
