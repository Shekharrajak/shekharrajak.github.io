---
layout: post
title: Coding Period Week 9
week: 17 July 2016 -  23 July 2016
posted_on: 21 July 2016
type: post
---

**Some points regarding trigonometric and inverse trigonometric functions in solveset :**

* There are many issues in solveset `solve_trig`.More inverse trigonometric formula and trigonometric identities should be defined/added or improved.
Also `simplify`, `trigsimp` and in `solveset` `_invert` methods should be improved accordingly.

* Some links, that is helpful to improve these functions.

    *  [https://en.wikipedia.org/wiki/Inverse_trigonometric_functions](https://en.wikipedia.org/wiki/Inverse_trigonometric_functions)
    *  [https://en.wikipedia.org/wiki/Proofs_of_trigonometric_identities](https://en.wikipedia.org/wiki/Proofs_of_trigonometric_identities)
    * [https://owlcation.com/stem/List-of-Inverse-Trig-Function-Identities-Integrals-and-Derivatives](https://owlcation.com/stem/List-of-Inverse-Trig-Function-Identities-Integrals-and-Derivatives)

* `trigsimp` must be more powerful so that `solve_trig` get simplified eq. (which solves trig equation by converting them into its `exp` form).

* `solve_trig` solves the trig eq. using its `exp` form. There may be cases when that `exp` form is complicated and solveset fail to handle that form.
There should be technique to convert that complicated form to simpler form(if possible) and then call the `solveset_complex`. That may help to improve the `solve_trig` method.

* We can use `_osbornei`, `hyper_as_trig` methods defined in `simplify/fu.py` to convert hyperbolic function to trigonometric function, then we can use `trigsimp` (we can't use `trigsimp` for hyperbolic functions).

* First need to improve basic concepts and add more identities. I opened a new PR to improve `rewrite` for trigonometric functions , PR is [#11424](https://github.com/sympy/sympy/pull/11424/).

--------------------------------------------------------------------------------

**eliminate() :**

* issue [#2720](https://github.com/sympy/sympy/issues/2720) : We need some kind of eliminate function, like [http://reference.wolfram.com/mathematica/ref/Eliminate.html](http://reference.wolfram.com/mathematica/ref/Eliminate.html). See also [http://stackoverflow.com/q/20826969/161801 ](http://stackoverflow.com/q/20826969/161801)

* It looks something related to [substitution](https://github.com/sympy/sympy/pull/11111/files#diff-eec0422923e8f100745c015cd8fdd6cfR1135) function.
But they are not same. Using `eliminate()` we will try to remove the variable(s) from the each equations(not solving the eq).

* Plan : First choose eq that have min. variables and get the value of the variable, to be eliminated. Go further and `subs` the value to next min. variable eq., and so on.

* Work in progress.

--------------------------------------------------------------------------------

**Meanwhile :**

* I found some basic issues in `ComplexInfinity` and trying to solve them in this PR [#11409](https://github.com/sympy/sympy/pull/11409).

* there may be many things to be added about `ComplexInfinity`, one can refer this link to implement them :
[http://reference.wolfram.com/language/ref/ComplexInfinity.html](http://reference.wolfram.com/language/ref/ComplexInfinity.html).

--------------------------------------------------------------------------------

***continue..***

--------------------------------------------------------------------------------
