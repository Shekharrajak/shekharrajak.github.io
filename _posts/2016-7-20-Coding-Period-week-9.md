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

* E.g 
--------------------------------------------------------------------------------

**Meanwhile :**

* I found some basic issues in `ComplexInfinity` and trying to solve them in this PR [11409](https://github.com/sympy/sympy/pull/11409).

* there may be many things to be added about `ComplexInfinity`, one can refer this link to implement them :

http://reference.wolfram.com/language/ref/ComplexInfinity.html
