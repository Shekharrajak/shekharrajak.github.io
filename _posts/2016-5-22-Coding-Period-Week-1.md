---
layout: post
title: Coding Period Week 1
week: 23 May 2016 - 28 May 2016
posted_on: 22 Mayl 2016
type: post
---
### nlinsolve continue

* You can read the problems in old solver `_solve_system` in [previous blog](http://shekharrajak.github.io/Community-Bonding-Period/) , if you haven't.

**PR [nlinsolve](https://github.com/sympy/sympy/pull/11111)**

**How it is better than old solver _solve_system :**

* **Positive dimensional system solver :** `nlinsolve` can return solution for positive dimensional system.
**How :** After reading articles on positive dimensional system and analyzing elimination method. I found that if we know Groebner Basis of the positive dimensional system (calling it as basis) then we can start solving equation(having least number of variable first in the basis) using `solveset` and substituting that solved solutions into other equation to get solution in terms of minimum variables.
Here the important thing is how we are substituting the known values and in which equations.

* **Complex solution in general form :** `nlinsolve` can return solution in general form .
**How :** If all the equations are not [polynomial equations](http://www.mathwarehouse.com/algebra/polynomial/polynomial-equation.php) means after solving Polynomial equations using `solve_poly_system` go to substitution method (defined in solveset) with this solution and solve for unsolved variables. In between to solve for particular variable `solveset` is used. When it find real solution then further steps will be using this real solution. If no real solution then it go for complex solution if it is found then extract the expression from the `imageset` and use it for further substitution. When solution is valid then add this general solution (solution in imageset) in the final result.

* **Complements will be added if any :** `nlinsolve` maintains `dict` to add complements for variables if any.
**How :** When there is infinite solution and `solveset` found complements during substitution method.
For example : solution = `{a : 1/d, b : -d, c : -1/d, d : d}` then in complements `dict {d : 0}` will be maintained and the final solution `{a : 1/d, b : -d, c : -1/d, d : {d} \ {0}}` is returned.

* **Unknowingly added features :** `nlinsolve` can return solution for positive dimensional linear system and simple linear system. But I recommend to use it for linear systems, since `linsolve` can do far better than `nlinsolve` for linear system.
**How :** Since it is using Groebner basis (inside `solve_poly_system`) of the system for polynomial equations. If it fails for some equation then basis is used in substitution method. So it can solve positive dimensional linear system.

----------------------------------------------------------------------

### Trigonometric inequality solution in General form

Currently `solveset` returns solution for trigonometric inequalities in the range of 2*pi. Solveset is designed to return all the solution. So need improvement in inequality solver.

From current master branch `of SymPy`:
Extended answer should be :` 1/6 *(12*π*n - 7*π) < x < 1/6 (12*π*n + π), n ∈ Z`

**Idea:**
Solveset uses `solve_univariate_inequality` to solve univariate inequalities.

* It uses `solve` to get the singularities and solution for the expression = 0\. So if we want to get solution in general form then need to replace this old solver with `Solveset`.

* To solve a trig inequality, transform it into one or many trig inequalities. Solving trig inequalities finally results in solving basic trig inequalities.

* Step 1\. Transform the given trig inequality into standard form `R(x) > 0 (or < 0)`.
Example. The inequality `(cos 2x < 2 + 3sin x)` will be transformed into standard form:
`R(x) = cos 2x – 3sin x - 2 < 0`

Step 2\. Find the common period . The common period must be the least multiple of the periods of all trig functions presented in the inequality. The complete solution set must, at least, cover one whole common period.
Example. The trig inequality `R(x) = cos 2x – 3sin x - 2 < 0` has `2π` as common period
Example. The trig inequality `R(x) = sin x – cos x/2 - 0.5 > 0` has `4π` as common period.

Step 3\. Solve the trig equation `R(x) = 0` If R(x) contains only one trig function, solve it as a basic trig equation.
If` R(x)` contains 2 or more trig functions, there are 2 methods, described below, to solve it.

a. METHOD 1\. Transform `R(x)` into a product of many basic trig equations. Next, solve these basic trig equations separately to get all values of x that will be used in Step 4.
Example 8\. Solve: `cos x + cos 2x > - cos 3x (0 < x < 2π)`
Solution. Step 1\. Standard form: `R(x) = cos x + cos 2x + cos 3x > 0`
Step 2\. Common period: `2π`
Step 3\. Solve` R(x) = 0`\. Transform it into a product using Sum to Product Identity:
`R(x) = cos x + cos 2x + cos 3x = cos 2x (1 + 2cos x) = 0.`

b. METHOD 2\. This method transforms a trig inequality with 2 or more trig functions into a trig inequality having only one trig function (called t) as variable. Next, solve for t from this trig equation, as a basic trig equation. Then, solve for x from these values of t.
chosen as function variable are: `sin x = t; cos x = t; cos 2x = t; tan x = t; and tan x/2 = t`.
Example 10\. Solve: `3sin² x = sin 2x + cos² x`
Solution. Divide both sides by `cos² x (cos x ≠ 0; x ≠ π/2)`. Let `tan x = t`.
`3 t² – 2t - 1 = 0`\. This is a quadratic equation having 2 real roots: 1 and -1/3
Next, solve the 2 basic trig equations: `tan x = t = 1`, and `tan x = t = -1/3`
Use `decompogen` defined in `sympy/solvers`

Step 4\. Solve the trig inequality `R(x) < 0 (or > 0)`. Then express the solution set in the form of intervals. Based on the found values of `x` from Step 3, solve, algebraically, the trig inequality` R(x) < 0 (or > 0)` by separately solving each basic trig inequality `f(x), g(x) .`., and then by setting up a sign table (sign chart). In final solution extend this with n*(common period).

### Domain and Range

**Function'domain :**

If a function does not model data or verbal conditions, its domain is the largest set of real numbers for which the value of is a real number. Exclude from a function’s domain real numbers that cause division by zero and real numbers that result in an even root of a negative number.

**Range:**

Values, the function can give.

* . The domain of is the set of all real numbers that are common to the domain of and the domain of Thus, we must find the domains of and before finding their intersection.

**The Composition of Functions**

The composition of the function with is denoted by and is defined by the equation
`(f*g)(x) = f(g(x))``
The domain of the composite function is the set of all such that
1\. `x` is in the domain of `g` and
2\. `g(x)` is in the domain of `f`.

The following values must be excluded from the input
• If `x` is not in the domain of g, it must not be in the domain of `f*g`
• Any `x` for which `g(x)` is not in the domain of `f`, must not be in the domain of `f*g`.

**Problems :**

* Finding common period of the complicated expressions. We can use LCM of

* finding domain/range.

**Reference**

* [Domain and range , function decomposition](http://miamibeachhigh.schoolwires.com/cms/lib07/FL01000126/Centricity/Domain/261/Ch1_Section7.pdf)
* [Squre root domain and range](http://web.fscj.edu/Lyn.Noble/mac1105/Wrksht/DomainRange.pdf)
* [Domain range](http://web.fscj.edu/Lyn.Noble/mac1105/Wrksht/DomainRange.pdf)
* [Inequality Trig Function](http://api.ning.com/files/n7ZUxQJY0YvfdRhhyH9DefMJ7cW08TWE8*egZvne-ZkVLkiWu1DzglvTH-7oM7zryLg7OSdRWmrEpVOlUHVHLLWtWkPhF11w/SOLVINGTRIGONOMETRICINEQUALITIESMETHODSANDSTEPS.pdf)
* [Trig Function , domain extended intervals](http://www.shsu.edu/kws006/Precalculus/4.9_Pythagorean_Identities_files/S%26Z%2010.7.pdf)

### nlinsolve XFAIL try

* solveset_real have some issues with expression having sqrt. It is returning some answer instead of `S.EmptySet`.

`solveset(20*sqrt(y**2 + (sqrt(-(y - 10)*(y + 10)) + 10)**2) - 60, y, S.Reals)`
this is returning

```
⎧-3⋅√391    3⋅√391⎫
⎨────────,  ──────⎬
⎩ 20         20   ⎭
```

But original answer is `emptyset`.

* Another thing is we are converting expressions into polynomial using `.as_poly(*symbols, extension=True)` so need to remove extra solution. code is added for this and works fine.
