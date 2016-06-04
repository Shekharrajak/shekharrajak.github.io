---
layout: post
title: Coding Period Week 2
week: 29 May 2016 - 4 June 2016
posted_on: 1 June 2016
type: post
---

### System of Inequalities

* Right now solve uses reduce_inequalities to solve system of equations. But it is not designed for more than one variable.

* ex: system = `[2*x - 3*y <= 12, x+5*y <=20, x>0] symbols = [x,y])  `
you will get :  
`NotImplementedError`:  
inequality has more than one symbol of interest  
We know answer is `[0 < x <120/13 and 2(x-6)/3 <= y <= (20-x)/5]`  
`[x = 120/13 and y = 28/13]`

* But `SymPy` already have project on this [Cylindrical algebraic decomposition](https://github.com/sympy/sympy/wiki/GSoC-2016-Ideas#cylindrical-algebraic-decomposition) to Provide an interface for solving systems of polynomial inequalities.

### General solution for Trigonometric equations

* PR [#11188](https://github.com/sympy/sympy/pull/11188)

* solveset(sin(x)-y, x ) doesn't work right now. But we know we can get solution using invert_real.

* In this PR `solveset_real(tan(x), x)` returns `imageset(Lambda(n, pi*(n - 1)), S.Integers)`
but I want `imageset(Lambda(n, n*pi), S.Integers)`.

* I added `reduce_imageset` in `solveset.py` to reduce the number of union returned by `_solve_trig` method. As Harsh said it is
no specific to `solveset`, so I moved the method to `sets/sets.py`. I added the doctests and test-cases in `test_sets.py`.

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

     
