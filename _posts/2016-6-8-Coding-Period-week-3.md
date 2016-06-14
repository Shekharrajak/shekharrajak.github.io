---
layout: post
title: Coding Period Week 3
week: 5 June 2016 - 11 June 2016
posted_on: 8 June 2016
type: post
---

### Continue: Simplified solution for Trigonometric Equation:


PR [#11188](https://github.com/sympy/sympy/pull/11188)


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

* I implemented the above order and shifted the `reduce_imageset` method in `_union` for `ImageSet`.
I created `_union_simiplify` a helper method for `_union` .

**`_union_simplify` better than my previous implementation :**

* Previous implementation was returning solution in simplified `ImageSet`, although it passed the all
test-case except 2-3 cases. But these 2-3 test-cases taught me you are doing over simplification.
So now I understood that we should not simplify the `ImageSet(s)` of the one factor solution, it may get simplified
with other factor solution ImageSet(s).

* Simplify them if there is difference of `pi`, that means club [(2*n + 1) and (2*n) => (n*pi)] or [(2*n* + 1)
and (2*n*pi + 2) => (n*pi)].


**So now _solve_trig uses factor_list for trig eq and then solve each factor F_i. To solve each factor F_i first do
F_i.rewrite(exp) and get this exp form factors F_ij so now the unnecessary exp will come out that dont contribute in
final solution. That's why we get simplified `ImageSet` that will be Union with previous solution. Inside the
Union => _union => _union_simplify checks for simplification with already present `ImageSet`. This is the process
till last factor F_i.**


**Meanwhile :**

* After working on blog for 1 week created my own blog template powered by Jekyll. and shifted the old blog into github.
PR for the blog link update in planet: [pull/42](https://github.com/sympy/planet-sympy/pull/42)

* I edited my old template(already hosted on [s-hacker.info](http://s-hacker.info)) to make it mobile responsive. Now it works perfectly for mobile. [shekharrajak.github.io](http://shekharrajak.github.io/)

* Found a issue in `factor_list`. [issues/11198](https://github.com/sympy/sympy/issues/11198) , When I passed
`f = sqrt(2)*sin(x) -1` into `solveset` I got this problem.

* To solve `factor_list` issue I opened a PR [pull/11201](https://github.com/sympy/sympy/pull/11201).
