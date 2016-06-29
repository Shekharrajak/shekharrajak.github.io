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

1. Currently, following five types of Diophantine equations can be solved using `~sympy.solvers.diophantine.diophantine` and other helper functions of the Diophantine module.


- Linear Diophantine equations:

`a1*x1 + a2*x2 + ... + an*xn = b`.

- General binary quadratic equation:

 `ax^2 + bxy + cy^2 + dx + ey + f = 0`

- Homogeneous ternary quadratic equation:

`ax^2 + by^2 + cz^2 + dxy + eyz + fzx = 0`

- Extended Pythagorean equation:

`a_{1} * x_{1}^2 + a_{2} * x_{2}^2 + ....  + a_{n} * x_{n}^2 = a_{n+1} * x_{n+1}^2`

- General sum of squares:

`x_{1}^2 + x_{2}^2 + \ldots + x_{n}^2 = k`

2. If I am correct then `Diophantine` returns all the soln if eq is Linear Diophantine equations, General binary quadratic equation and Homogeneous ternary quadratic equation. I tried some Linear Diophantine equations and cross checked with online Diophantine solvers.

3. In last 2 (Extended Pythagorean equation and General sum of squares) we need to do `permute_signs` to get all the soln.

E.g.

```
    >>> from sympy.utilities.iterables import permute_signs
    >>> list(permute_signs((1, 12)))
    [(1, 12), (-1, 12), (1, -12), (-1, -12)]

```

4. `classify_diop` can returns these `diop_type` :

- linear
- univariate
- binary_quadratic -> permute sign
- inhomogeneous_ternary_quadratic
- homogeneous_ternary_quadratic_normal
- homogeneous_ternary_quadratic
- inhomogeneous_general_quadratic
- inhomogeneous_general_quadratic
- homogeneous_general_quadratic
- general_sum_of_squares ->permute sign
- general_pythagorean
- cubic_thue
- general_sum_of_even_powers ->permute sign

 If the equation type is none of these then `solveset_integers` should returns `ConditionSet`.Because currently `diophantine`
 can handle these kinds of eq only

--------------------------------------------------------------------------------


**continue...**
