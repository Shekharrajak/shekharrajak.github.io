---
layout: post
title: Coding Period Week 5
week: 19 June 2016 - 25 June 2016
posted_on: 21 June 2016
type: post
---


**Continue- nonlinsolve :**

PR [#11111](https://github.com/sympy/sympy/pull/11111)

* I found the case where complex solution may be missed. When `solve_poly_system` is solving polynomial equation and that result is used
in solving non polynomial-equation. May be `solve_poly_system` returned only real solution( so complex solution is not be used for further steps) so further step is with this real solution.

* It seems `solve_poly_system` is doing it's job since it is not designed for all solution. But we have `substitution` method using
`solveset_real` and `solveset_complex` and retuning all solutionn. In new commits I improved the code and now `substitution` method can solve all kind of system independently.

* I come across these kind of situation many times :

```
In [68]: x, y, z, r, t = symbols('x, y, z, r, t', real = True)

In [69]: soln = solveset(sqrt(r)*Abs(tan(t))/sqrt(tan(t)**2 + 1) + x*tan(t),x,S.Reals)

In [70]: soln
Out[70]:
          ⎧      √r⋅│tan(t)│      ⎫
(-∞, ∞) ∩ ⎪───────────────────────⎪
          ⎨   _____________       ⎬
          ⎪  ╱    2               ⎪
          ⎩╲╱  tan (t) + 1 ⋅tan(t)⎭

In [71]: soln = solveset(sqrt(r)*Abs(tan(t))/sqrt(tan(t)**2 + 1) + x*tan(t),x)

In [72]: soln
Out[72]:
⎧     -√r⋅│tan(t)│      ⎫
⎪───────────────────────⎪
⎨   _____________       ⎬
⎪  ╱    2               ⎪
⎩╲╱  tan (t) + 1 ⋅tan(t)⎭

```
In other words :

```
In [1]: Intersection(FiniteSet(-x), S.Reals)
Out[1]: (-∞, ∞) ∩ {x}

In [2]: Intersection(FiniteSet(x), S.Reals)
Out[2]: ℝ ∩ {x}

```

So I am not able to extract the `-x` here. Because of this `nonlinsolve` returning some extra soln.
One case is in test file : `test_issue_5132`.

I opened a PR for this [#11280](https://github.com/sympy/sympy/pull/11280)

* If someone wants to see the changes I did in `nonlinsolve` then check these gist [nonlinsolve_till_24june_2016](https://gist.github.com/Shekharrajak/5e77fe344c996c17c177985853884985),
[nonlinsolve_till_21jun2016.py](https://gist.github.com/Shekharrajak/5d285ce0cf113cfc217c3e33c3ca04c0).

**previous PRs update :**

* [#11188](https://github.com/sympy/sympy/pull/11188) - Simplified Solution for Trigonometric equation :
 I did some minor changes.Now I hope it is good to go.

* [#11234](https://github.com/sympy/sympy/pull/11234) - Connecting Diophantine and solveset to get Integer solution:
added some testcases. I have defined `solveset_integers` for this, it take take list of symbols(to get soln in that order).t
But Currently solveset takes one symbol. I hope this PR is good to go.

* [11257](https://github.com/sympy/sympy/pull/11257) - solveset univariate trig inequality solvers : Actually to simplify the
soln I need to use PR [#11188](https://github.com/sympy/sympy/pull/11188), so if it got merged that code will help me in this PR.


--------------------------------------------------------------------------------

**Meanwhile :**

* I worked on these previous PRs regarding issues I reported [#11239](https://github.com/sympy/sympy/pull/11239), [11280](https://github.com/sympy/sympy/pull/11280).

--------------------------------------------------------------------------------
**continue..**
