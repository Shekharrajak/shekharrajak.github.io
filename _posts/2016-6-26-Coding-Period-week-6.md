---
layout: post
title: Coding Period Week 6
week: 26 June 2016 -  2 July 2016
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

    `x_{1}^2 + x_{2}^2 + ... + x_{n}^2 = k`

    2. If I am correct then `Diophantine` returns all the soln if eq is Linear Diophantine equations, General binary quadratic equation and Homogeneous ternary quadratic equation. I tried some Linear Diophantine equations and cross checked with online Diophantine solvers(one of the solver is [here](http://www.numbertheory.org/php/main_pell.html)).

    3. In last 2 (Extended Pythagorean equation and General sum of squares) we need to do `permute_signs` to get all the soln.

    E.g.

        ```
            >>> from sympy.utilities.iterables import permute_signs
            >>> list(permute_signs((1, 12)))
            [(1, 12), (-1, 12), (1, -12), (-1, -12)]

        ```

    In general if all variables have even powers then we should do `permute_signs`. `Diophantine` solves the factors of the eq
    so if we have eq like this `x**2 - y**2`, diophantine solves factors `x + y` and `x - y`.


        ```

          >>> from sympy.solvers.diophantine import diophantine
          >>> from sympy.abc import x, y, z
          >>> diophantine(x**2 - y**2)
          set([(-t_0, -t_0), (t_0, -t_0)])

        ```

    so we should check even powers and permute sign.

    other examples :


    ```

      >>> from sympy.solvers.diophantine import diop_general_sum_of_squares
      >>> from sympy.abc import a, b, c, d, e, f
      >>> diop_general_sum_of_squares(a**2 + b**2 + c**2 + d**2 + e**2 - 2345)
      set([(15, 22, 22, 24, 24)])

      >>> from sympy.solvers.diophantine import diop_general_pythagorean
      >>> diop_general_pythagorean(a**2 + b**2 + c**2 - d**2)
      (m1**2 + m2**2 - m3**2, 2*m1*m3, 2*m2*m3, m1**2 + m2**2 + m3**2)
      >>> diop_general_pythagorean(9*a**2 - 4*b**2 + 16*c**2 + 25*d**2 + e**2)
      (10*m1**2  + 10*m2**2  + 10*m3**2 - 10*m4**2, 15*m1**2  + 15*m2**2  
        + 15*m3**2  + 15*m4**2, 15*m1*m4, 12*m2*m4, 60*m3*m4)

      >>> from sympy.solvers.diophantine import diop_general_sum_of_even_powers
      >>> diop_general_sum_of_even_powers(a**4 + b**4 - (2**4 + 3**4))
      set([(2, 3)])

    ```

    In above these types of cases we need `permute_signs`. If we check these solution you can see that `permute_signs`
    is needed when solutions is not parameterized.

    e.g.


    ```

        >>> from sympy.solvers.diophantine import diophantine
        >>> from sympy.abc import x, y, z
        >>> diophantine(x**2 - y**2)
        set([(-t_0, -t_0), (t_0, -t_0)])

    ```

    solution `set([(-t_0, -t_0), (t_0, -t_0)])` is same as `set([(-t_0, -t_0), (t_0, t_0), (-t_0, t_0), (t_0, -t_0)])`.(because `t_0` can take any integer value.)

    I discussed these things with [@thilinarmtb](https://github.com/thilinarmtb) (He have worked on `diophantine`. Blog link : [https://thilinaatsympy.wordpress.com/](https://thilinaatsympy.wordpress.com/page/2/)). Main points are :

      Only the linear solver is incomplete, the algorithm in Diophantine module should be fixed (`permute_signs` or something like that won't help). We can use `permute_signs` when we have even powers in all variables. We should update Diophantine module to use permute sign. But we should not returns `ConditionSet` for linear diophantine eq. because for linear diophantine eq `diophantine()`returns parameterized solution which is complete most of the time.

    4. `classify_diop` can returns these `diop_type` :

        - linear
        - univariate
        - binary_quadratic
        - inhomogeneous_ternary_quadratic
        - homogeneous_ternary_quadratic_normal
        - homogeneous_ternary_quadratic
        - inhomogeneous_general_quadratic
        - inhomogeneous_general_quadratic
        - homogeneous_general_quadratic
        - general_sum_of_squares
        - general_pythagorean
        - cubic_thue
        - general_sum_of_even_powers

     If the equation type is none of these then `solveset_integers` should returns `ConditionSet`.Because currently `diophantine`
     can handle these kinds of eq only.


* PR Update diophantine to get some missing solution: [11334](https://github.com/sympy/sympy/pull/11334)

--------------------------------------------------------------------------------

**Continue simplified Trigonometric eq solution :**

* shifted the `_union_simplify` function code to `_union` in `fancyset/ImageSet` with some changes.

--------------------------------------------------------------------------------
**continue...**
