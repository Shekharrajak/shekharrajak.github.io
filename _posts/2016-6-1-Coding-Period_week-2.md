---
layout: post
title: Coding Period Week 2
week: 29 May 2016 - 4 June 2016
posted_on: 1 June 2016
type: post
---

### System of Inequalities

* Right now solve uses `reduce_inequalitie`s to solve system of equations. But it is not designed for more than one variable.

* ex: system = `[2*x - 3*y <= 12, x+5*y <=20, x>0] symbols = [x,y])  `
you will get :  
`NotImplementedError`:  
inequality has more than one symbol of interest  
We know answer is `[0 < x <120/13 and 2(x-6)/3 <= y <= (20-x)/5]`  
`[x = 120/13 and y = 28/13]`

* But `SymPy` already have project on this [Cylindrical algebraic decomposition](https://github.com/sympy/sympy/wiki/GSoC-2016-Ideas#cylindrical-algebraic-decomposition) to Provide an interface for solving systems of polynomial inequalities.

* If we want to feature like old `solve` then just need to pass system of inequalities having one variable to solve
for one variable. After checking this use `reduce_inequalitie(system, symbol)` it will return solution. It is easy to implement.

### General solution for Trigonometric equations

* PR [#11188](https://github.com/sympy/sympy/pull/11188)

* Previous work in this problem : [#10898](https://github.com/sympy/sympy/pull/10898),
[#10713](https://github.com/sympy/sympy/pull/10713), [#10733](https://github.com/sympy/sympy/pull/10733)

**Problems in old method :**

* `_solve_trig` changes the trig equation in `exp` form (it's fine). But then fraction and solving equation
for it's parts makes more number of `exp`. If we have more number of `exp` then we get more number of `imageset`,
Since we `_invert` for each `exp` factors.

* It retuns `ConditionSet` when it can't solve, but its expression is in ` exp` form mostly with `I` and
in complicated form.

* some times `_solve_as_poly` can solve Trig equations, but it is not using it.

**New implemention :**

* I added `reduce_imageset` in `solveset.py` to reduce the number of union returned by `_solve_trig` method. As Harsh said it is
no specific to `solveset`, so I moved the method to `sets/sets.py`. I added the doctests and test-cases in `test_sets.py`.

* Now solving the `exp` form directly using `solveset`. This makes the less number of `ImageSet` in many cases.
But to solve equation having `tan` in it, will be complicated, for that I changed the `solve_rational` method,
so that it can handle  `exp` with `I`. in denominator.

* Now using `_solve_as_poly` when `solveset` can't solve it using `exp` form. If this also can't solve then retuns
the `ConditionSet` having simple trig functions, which is understandable.


**reduce_imageset :**

* `reduce_imageset` take the `ImageSet` or Union of `ImageSet` and returns the minimum number of `ImageSet`.

* First we extract the `Lambda` expression from the each `ImageSet` and take principle values. Separate the positive and negative principle values and sort them.

* +ve and -ve values are passed into `interpolate` method defined in `polys/polyfuncs.py` to get the general function in terms
of Dummy `n`.

* If only one `Imageset` or value in +ve or -ve value list then return that as it is. Here we need to note that Dummy `n` defined here
is different then original lambda expression, so need to return original `imageset`. So I am storing original `ImageSet` in dict with
its principle vales.

* If more than one +ve/-ve values are there then interpolate expression will be `ImageSet` expression and return.

* Here I separe the -ve and +ve values because interpolate returns complicated expressions if we both types of values.

* Also I sorted the +ve and -ve list, to get simplified expression from interpolate.

**Problems :**

* In this PR `solveset_real(tan(x), x)` returns `imageset(Lambda(n, pi*(n - 1)), S.Integers)`
but I want `imageset(Lambda(n, n*pi), S.Integers)`.

**Issues :**

* Meanwhile I found a issue in `solveset`. [issues/11194](https://github.com/sympy/sympy/issues/11194).
`2*sin(x) - 2*sqrt(3)*cos(x) - sqrt(3)*tan(x) +3 = 0` can be easily solved if we factorize it correctly. But I haven't found
a good way to get its factor. I tried `factor`, `expand(Trig + True)` , `expand_trig`, `rewrite(sin)`.
