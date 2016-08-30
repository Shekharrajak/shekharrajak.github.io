---
layout: post
title: Coding Period Week 13 - Last week and conclusion
week: 16 August 2016 -  22 August 2016
posted_on: 21 August 2016
type: post
---

--------------------------------------------------------------------------------

**Documentation nonlinsolve:**

PR [#11532](https://github.com/sympy/sympy/pull/11532)

--------------------------------------------------------------------------------

**Conclusion :**

So the GSoC coding period is going to end. Here I am writing what I did, my todo list and suggestions for future work.

* One can see the progress report of each week and minutes of meeting here :
[GSoC-2016-Solvers-Progress](https://github.com/sympy/sympy/wiki/GSoC-2016-Solvers-Progress)

* My all the PRs link is here : [sympy/pulls/shekharrajak](https://github.com/sympy/sympy/pulls?utf8=%E2%9C%93&q=is%3Aopen%7Cclosed%20is%3Apr%20author%3AShekharrajak%20)

* I have created a vertical timeline to show all the work in chrononical order in this link : [timeline](http://shekharrajak.github.io/gsoc16_final.html)

--------------------------------------------------------------------------------

**Meanwhile :**

* I find one issue : [#11534](https://github.com/sympy/sympy/issues/11534) in mailing list discussion. This shows that we need better
`invert` method for inverting nested roots/powers equtions in `solveset` .

* and this [#11528](https://github.com/sympy/sympy/issues/11528). `factor_list` will be helpful in factoring the equation in `solveset` and solve for it factors and union the solution(during the PR #11188 discussion with Harsh this idea came out). It will actually replace the [elif f.is_Mul and all(_is_finite_with_finite_vars(m, domain)](https://github.com/sympy/sympy/blob/master/sympy/solvers/solveset.py#L646) statement in `_solveset` and `factor_list` will be used soon.
