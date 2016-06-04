---
layout: post
title: Community Bonding Period
week: Community Bonding Period( 23 April 2016 - 30 April 2016)
posted_on: 22 May 2016
type: post
---

# Week 1 ( 23 April 2016 - 30 April 2016)

## Excited about my GSoC Blog


I created my blog on around Nov-Dec 2015, mostly for GSoC ( confident :p ). But the template was still on github with random contents. [Blog repo](http://github.com/shekharrajak/MyBlog)

So it was the time to replace these contents and edit the template and host on my personal site

On 23 April 2016 00:30 (IST) GSoC projects are announced, next day in the evening I edited the blog template and made it for GSoC. I added two posts ( contribution before GSoC and project) and hosted late night.

In this week I had Lab exams and Minor tests also. I had some chat/Email with the mentors about the project as well.

# Week 2, 3 ( 1 May 2016 - 14 May 2016)

It was End Examination time ( 5 - 12 May). In this period I tried to be active in gitter chat and Mailing list. I worked on my previously opened PRs and new issues.

Some of them are : [pull/10733](https://github.com/sympy/sympy/pull/10733), [pull/10550](https://github.com/sympy/sympy/pull/10550). I related some new issues with old PRs and tried to fix them.

I tried to add new feature in `decompogen` method in this PR [pull/11085](https://github.com/sympy/sympy/pull/11085)

We had first hangout on 2 May 2016 , in which [Kshitij](https://github.com/kshitij10496) and me choose our work for next week. I choose to work on Non Linear System of Equations and Multivariate Equation solver for `Solveset`.

Minutes of meeting is in Wiki page [GSoC-2016-Solvers-Progress#meeting-01](https://github.com/sympy/sympy/wiki/GSoC-2016-Solvers-Progress#meeting-01)

# Week 4, 5 ( 15 May 2016 - 23 May 2016)

After the End semester examination, we had 2nd meeting on [15 May 2016](https://github.com/sympy/sympy/wiki/GSoC-2016-Solvers-Progress#meeting-02). We ( [Harsh](https://github.com/hargup), [Amit](https://github.com/aktech), [kshitij](https://github.com/kshitij10496) and [me](https://github.com/shekharrajak)) discussed about what should be done before coming on meeting and documenting ideas/mplementation on blog or somewhere.

I started working on `nlinsolve` to solve Non Linear System of Equations.

## Auditing SymPy's non linear system of equation solver

A non-linear system of equations is a system in which at least one of the variables has an exponent other than 1 and/or there is a product of variables in one of the equations.

### How old Solver handle this :

* SymPy uses `_solve_system` function to solve all kind of systems( linear, non linear, Multivariate Equations).

* `_solve_system`, try to converts all the equations into Poly and checks for linear system.
If all the Poly equations are linear then solve this using minsolve_linear_system or solve_linear_system.

* If all the equations are not linear then` _solve_poly_system` try to solve them.
If system is not zero dimensional then returns `NotImplementedError`. `_solve_poly_system` uses Groebner basis of the system, when any one equation in the basis contains only symbol, then this reduced system is solvable.

* When solve_poly_system returns solutions for some variables, then one by one solve the equation using `solve` for
all the remain unsolved variables.

### Problems in old Solver method :

* `solve_poly_system` can return solution for zero-dimensional only. So when polynomial	Equation system is positive dimensional system (infinite solution) then `NotImplementedError` is returned by `_solve_poly_system`.

* Elimination, substitution and solve_poly_system is in one function `_solve_system`. So it is messy.

* When it solves for unsolved symbol, after substituting known values in the equation using `solve` then we don't get solution in general form. eg. if equation is sin(x) + y = 0 and known solution is y = -1 then solve returns pi/2.

* When it solves for unsolved symbol, after substituting known values in the equation using `solve` then we don't get solution in general form. eg. if equation is sin(x) + y = 0 and known solution is y = -1 then solve returns pi/2.

### My idea and implementation :

#### nlinsolve

I opened a PR [pull/11111](https://github.com/sympy/sympy/pull/11111) with initial code.

##### Idea :

* The main idea was to use `solve_poly_system` method ( sympy/solvers/polysys.py ) which works pretty well in old solvers, to solve zero-dimensional system.

* `solve_poly_system` is used to solve equations which are polynomial.

* If all the equations are polynomail and have finite solution (zero-dimensional) then `solve_poly_system` solve them.

* When system has all the equatons polynomial but not zero-dimensional then it has infinite number of solutions, To handle these system I thought about method used in this [PDF](http://people.math.gatech.edu/~aleykin3/math4803spr13/BOOK/chapter1.pdf) page: 9 , examples : 2.2

I implemented `nlinsolve_matrix` using these steps for 2 equations and 2 variables. The code can be found in this <a href="https://gist.github.com/Shekharrajak/a4ff089582f41b163f494a369cf51294"> gist </a>

<script src="https://gist.github.com/Shekharrajak/a4ff089582f41b163f494a369cf51294.js"></script>

This method give equation on `y` ( if 2 variables are `x` and `y`. Matrix created using coefficients of `x` power). But Matrix returns `0` for positive dimensional system ( I only checked for 2 equations 2 variables poisitive dimentional system). So we can't get an equation of `y`. After seeing this issue I didn't generalize this method for more equations and variables.</p>

* I read more about positive dimensional systems from Kshitij's proposal and internet. I found another way of solving them using RUR (Rational Univariate Representation), some good examples/PDFs are :

     * http://www.maplesoft.com/support/help/Maple/view.aspx?path=Groebner/RationalUnivariateRepresentation
     * http://www.m-hikari.com/imf-2010/5-8-2010/ayadIMF5-8-2010.pdf
     * href="http://research.cs.tamu.edu/keyser/Papers/AMSDimacs2005.pdf
     * http://homepages.math.uic.edu/~jan/mcs563/lec12.pdf

These links contains examples but not the clearly the methods for positive dimensional system.

* I am still finding a good way to get the RUR.

* If we have system in which some of the equations are polynomial and some are not then substitution method is best (I didn't find other symbolic way).

* First solve the polynomial equations if present for all the combinations of `symbols` according to the number of polynomial equations. Store the solutions with `symbols` in `dict`. Each solution may contains symbols that can be solved using substitution method.

* Now solve the non polynomial equations using knows solutions( one by one substitution of known solution ) and solve. After solving substitute in the previous solution if that symbol was in there.

* If number of equations and number of variables are equal then we get solution for each variable independently otherwise solutions may depend on each other.

* Work is still in progress for RUR and substitution method.

#### Problems I am facing :

**1.** How can we get RUR for the system of equation to get solution for +ve Dimensional.

**What I think :** After reading the articles and discussion with <a href="https://github.com/jksuom">@jksoum </a>, I found that Groebner basis and concepts of Gauss-Jordan method for linear systems is helpful to eliminate the variabels.<br> Now I am trying Groebner Basis of the system( which is reduced form and can be solved using proper substitution method). The main thing is elimination systematically and ordering of monomials.<br>After solving the groebner basis expressions we may get the answer.

**2.** Solveset may return Imageset/FiniteSet/Intersection/complement during substitution method.

**What I think :** Sometimes `solveset` returns real solution with intersection with `R` (-oo to oo) or in ImageSet. If solution is in ImageSet then need to check the expression ( if there is unsolved symbol in substitution steps).

If we get ConditionSet then `NotImplementedError`.

If we are solving `a + 1/d` for `d` then `solveset` will return` FiniteSet(-1/a)` complement `FiniteSet(0)`. so need to consider first args and store the complement in dict.

**3.** There may be Complex solution but no real solution so need to consider both complex and real solutions (inside substitution step) ?

**What I think :** For complex/real solution we will get next solution( after substituting that solution). Need to check complex solution if no real solution from `solveset` (inside substitution method)

**I continued the work and next week I tried to fix these problems and almost succeed.My further work on `nlinsolve` is [here](http://shekharrajakgithub.io/Coding-Period-Week-1/)**

## Solveset for non symbol

I opened a PR <a href="https://github.com/sympy/sympy/pull/11128">pull/11128</a> to add this feature.

### Idea :

* First detect the `symbol` ( for which we are solving equation ) is not a symbol and replace it with some temporary symbol in both `symbol` and `f` ( expression )

* We need to use Symbol only to replace, because all the other methods/functions are made for symbols .I realized this after failing many times :) .

* After this there may be non invertable terms like `Derivative`, `Integrals` ( `function` is not needed here). If want to solve for `f(x)` then `f(x)` is replaced from `symbol` and `f` as well.

I defined a method `check_noninverts(f, symbol)` for this.

* Now `solveset` treat them as Symbol and solves. At the end we need to replace back these temporary variables. For this I defined `swap_back(result, swapped_symbol, non_inverts)`.This works for ConditionSet also. Most of the time in Trigonometric Equations doesn't contains Non invertable terms so ImageSet was not needed.

* All checks have passed after little modifications.
