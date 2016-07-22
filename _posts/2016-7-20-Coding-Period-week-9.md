---
layout: post
title: Coding Period Week 9
week: 17 July 2016 -  23 July 2016
posted_on: 21 July 2016
type: post
---

**Some points regarding trigonometric and inverse trigonometric functions in solveset :**

* There are many issues in solveset `solve_trig`, which is because inverse trigonometric formula and trigonometric identities should be defined or improved
in `simplify`, `trigsimp` and in `solveset` `_invert` methods.

* Some links

    *  [https://en.wikipedia.org/wiki/Inverse_trigonometric_functions](https://en.wikipedia.org/wiki/Inverse_trigonometric_functions)
    *  [https://en.wikipedia.org/wiki/Proofs_of_trigonometric_identities](https://en.wikipedia.org/wiki/Proofs_of_trigonometric_identities)
    * [https://owlcation.com/stem/List-of-Inverse-Trig-Function-Identities-Integrals-and-Derivatives](https://owlcation.com/stem/List-of-Inverse-Trig-Function-Identities-Integrals-and-Derivatives)

* `trigsimp` must be more powerful so that `solve_trig` get simplified eq that can be through its `exp` form.

* `solve_trig` solves the trig eq. using its `exp` form. There may be cases when that `exp` form is complicated and solveset fail to handle that form.
There should be technique to convert that complicated form to simpler form(if possible) and then call the `solveset_complex`. That may help to improve the `solve_trig` method.

* We can use `_osbornei`, `hyper_as_trig` methods defined in `simplify/fu.py` to convert hyperbolic function to trigonometric function, then we can use `trigsimp` (we can't use `trigsimp` for hyperbolic functions).

* Need to improve basic concepts and add more identities. I opened a new PR to improve `rewrite` for trigonometric functions , PR is [11424](https://github.com/sympy/sympy/pull/11424/).


--------------------------------------------------------------------------------

**Meanwhile :**

* I found some basic issues in `ComplexInfinity` and trying to solve them in this PR [11409](https://github.com/sympy/sympy/pull/11409).

* there may be many things to be added about `ComplexInfinity`, one can refer this link to implement them :

http://reference.wolfram.com/language/ref/ComplexInfinity.html
