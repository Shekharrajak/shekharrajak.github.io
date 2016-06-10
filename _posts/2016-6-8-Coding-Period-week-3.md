---
layout: post
title: Coding Period Week 3
week: 5 June 2016 - 11 June 2016
posted_on: 8 June 2016
type: post
---

### Continue: Simplified solution for Trigonometric Equation:

**New Problems :**

* When I tried more testcases having sqrt and other types I found new issues on `reduce_imageset` method. Some of the Simplified
solutions contains undesired `n` values.

**Changes in solveset/_solve_radical**

* Sometimes `_solve_radical` may get `exp(I*x)` terms and solving them we give Imageset, I added the

```
if isinstance(result, ImageSet) or any(isinstance(r, ImageSet) for r in result.args):
        return result
```

in the method.

**Using `factor_list` in solve_trig :**

* There are many cases we can do factor of expression and solve each factor may give us more simplified solution.

* I added the `factor_list` and solving each factors and union the solution.

* When I analyzed how `exp` form is solved and found correct order to use `factor` or `factor_list` ,the summery
is in this [gist](https://gist.github.com/Shekharrajak/17fdcd2320f572fc9fc8674823137e20)

<script src="https://gist.github.com/Shekharrajak/17fdcd2320f572fc9fc8674823137e20.js"></script>

**Meanwhile :**

* After working on blog for 1 week created my own blog template powered by Jekyll. and shifted the old blog into github.
PR for the blog link update in planet: [pull/42](https://github.com/sympy/planet-sympy/pull/42)

* I edited my old template to make it mobile responsive. Now it works perfectly for mobile. [shekharrajak.github.io](http://shekharrajak.github.io/)

* Found a issue in `factor_list`. [issues/11198](https://github.com/sympy/sympy/issues/11198) , When I passed
`f = sqrt(2)*sin(x) -1` into `solveset` I got this problem.

* To solve `factor_list` issue I opened a PR [pull/11201](https://github.com/sympy/sympy/pull/11201).

**continue...**
**Trying to improve reduce_imageset method**
