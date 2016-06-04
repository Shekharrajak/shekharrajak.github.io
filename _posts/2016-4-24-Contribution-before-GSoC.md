---
layout: post
title: Contribution before GSoC
week: Sept 2015 -June 2016
posted_on: 24 April 2016
type: post
---

### SymPy :

[SymPy](http://www.sympy.org/en/index.html) is a Python library for symbolic mathematics. It aims to become a full-featured Computer Algebra System (CAS) while keeping the code as simple as possible in order to be comprehensible and easily extensible.

It was month of August 2015, when I was learning new libraries in python and somehow reached at Amit's blog about `SymPy` and his contribution to `SymPy`. I am very much interested in Mathematics so it was pretty amazing to see how `SymPy` is solving equations and doing mathematics using python.

### Joined gitter chat room :

The time I joined `SymPy` gitter chat room, I found many active contributors/developers replying the questions and discussing ideas. I didn't know how `SymPy` works and didn't work in Python previously. I started reading Documentations and Wiki Pages present in `SymPy` repository in github. I watched the videos and tried some problems myself, but doing only these things would not help.
I started participating in gitter chat discussion, give answer whatever I knew and questioned whenever I had doubts. These became my everyday work.
Slowly I understood the modules and code organization of `SymPy`.But there were still something I didn't know, that's why I was not able to send any patches/Pull Request in github `SymPy` repo till Nov-Dec 2015.

### Started sending Pull Request

I had been active in `SymPy` gitter chat room for around 3 month but still struggling to fix a bug. I tried most of the easy bugs but didn't understand where is the problem in the code.

So I started fixing Documentation bugs and formating. But I wanted to fix bugs related to code.

One day someone was discussing about debugger tool. He was also getting difficulty in understanding the code. I read some articles and started using PuDB.

PuDB works very well and easy to work with it. I restarted exploring the easy bugs and using debugger it was pretty easy to detect the line where the problem was.

### Contribution started now

Okay, so after learning these many thing I was very much interested about `SymPy`, because I almost understood how the Open Source Developers work. I enjoyed my days fixing/trying to fix bugs in SymPy. All the day I think about the bug and try to solve them. I enjoyed a lot in this period. It was around Dec 2015 ,Jan 2016.

### Merged/Open/Closed contributions in chronological order before GSoC 2016

[#10215](https://github.com/sympy/sympy/pull/10215) : some Usage/examples for `srepr` and added some lines to show how `repr` different from `srepr` printing.

[#10311](https://github.com/sympy/sympy/pull/10311) : Projects using `SymPy` in docs.

[#10312](https://github.com/sympy/sympy/pull/10312) : [#10215](https://github.com/sympy/sympy/pull/10215) extended and added more usage/examples for `srepr`.

[#10314](https://github.com/sympy/sympy/pull/10314/) : Dot printing examples and usage.

[#10319](https://github.com/sympy/sympy/pull/10319/) : Addition of namespaces, namespaces_default, translation for `SciPy` in `lambdify.py`.

[#10330](https://github.com/sympy/sympy/pull/10330) : removal of `guide.rst`.

[#10333](https://github.com/sympy/sympy/pull/10333) : better comment at `SymPy/interactive/tests/test_print_builtin_option`.

[#10370](https://github.com/sympy/sympy/pull/10370) : `math.fabs()` converts its argument to float if it can (if it can't, it throws an exception). It then takes the absolute value, and returns the result as a float. Fixes [#9474](https://github.com/sympy/sympy/issues/9474)

[#10385](https://github.com/sympy/sympy/pull/10385) :`SymPy` treated symbols having `zero = True` assumption as non-negative & non-positive & real. But `SymPy` don't know; that is 0.It was not defined anywhere in `SymPy`. Previously line `x = Symbol('x' ,zero=True)`, `x` was treated as symbol only, during execution and didn't took its value.
 Fixes [#8167](https://github.com/sympy/sympy/issues/8167)

[#10407](https://github.com/sympy/sympy/pull/10407) : In `NumPy``amin` is defined as `numpy.amin(a, axis=None, out=None, keepdims=False)` So if we use `Min` and `Numpy` is installed in the system. Then `SymPy` use `NumPy` for` lambdify` method. So when we pass `l(1, 2, 3)` Then it takes ` a =1 ,axis=2,out=3` where a is list of numbers for which we want minimum. `SymPy` mapping with `NumPy` `amin` is not correct.

[#10444](https://github.com/sympy/sympy/pull/10444) : Integration of summation type expressions.
Fixes [#7827](https://github.com/sympy/sympy/issues/7827)

[#10460](https://github.com/sympy/sympy/pull/10460) : `Solveset` is now able to solve `XFAIL` `test_issue_failing_pow`. `assert solveset(x**(S(3)/2) + 4, x, S.Reals) == S.EmptySet`.

[#10482](https://github.com/sympy/sympy/pull/10482) : This is able to give solutions in reduced/simplified and known easy form in many cases. Fixes [#9824](https://github.com/sympy/sympy/issues/9834) , [#10426](https://github.com/sympy/sympy/issues/10426)

[#10494](https://github.com/sympy/sympy/pull/10494) : Few lines added in docs for `Singleton` `S`.

[#10502](https://github.com/sympy/sympy/pull/10502) : Needed a list which stores about if particular `cond` solution is added or not. Otherwise it may not add result , like previously if `cond` solution is not added but still [if condition] true (for this particular issue's testcase) and then it will mark `matches_other_piece = True` so this solution couldn't be added into result.
Fixes [#10122](https://github.com/sympy/sympy/issues/10122)

[#10542](https://github.com/sympy/sympy/pull/10542) : Need to pass if integral have symbolic upper and lower bound. Fixes : [#10434](https://github.com/sympy/sympy/issues/10434)

[#10547](https://github.com/sympy/sympy/pull/10547) : Problem was `Solveset` assuming that condition symbol is same as symbol for which it is finding solution. so there was problem when condition doesn't contains the solution symbol. Now is storing the symbols of condition and defining the interval accordingly for all the symbols.
Fixes : [#10534](https://github.com/sympy/sympy/issues/10534)

[#10550](https://github.com/sympy/sympy/pull/10550) : solveset_real need to check symbol in piecewise-condition.Expression with multiple abs ,having Piecewise solution as 0.
 Fixes : [#10122](https://github.com/sympy/sympy/issues/10122) and [#10534](https://github.com/sympy/sympy/issues/10534)

[#10552](https://github.com/sympy/sympy/pull/10552) :`Solveset` hyperbolic Functions.


```
#  complex solution
>>>> solveset(sinh(x))
{n⋅ⅈ⋅π | n∊ ℤ}
# Real solution
>>>> solveset(sinh(x), x, S.Reals)
{0}

```

Fixes [#9531](https://github.com/sympy/sympy/issues/9531) , [#9824](https://github.com/sympy/sympy/issues/9824) , [#10426](https://github.com/sympy/sympy/issues/10426), [#7914](https://github.com/sympy/sympy/issues/7914) and [#9606](https://github.com/sympy/sympy/issues/9606)

[#10575](https://github.com/sympy/sympy/pull/10575) : `linsolve` now able to solve unsimplified equations having constant variable. Fixes : [#10568](https://github.com/sympy/sympy/issues/10568)

[#10579](https://github.com/sympy/sympy/pull/10579): modified domain range if denominator is zero. Fixes [#8715](https://github.com/sympy/sympy/issues/8715)

[#10622](https://github.com/sympy/sympy/pull/10622) : Decompogen checking whether function contains `symbol` or not.

[#10649](https://github.com/sympy/sympy/pull/10649): replacing solver in some module.

[#10689](https://github.com/sympy/sympy/pull/10689): Real solution for some `const**(symbol)` type equation.
Fixes Real solution for [#10688](https://github.com/sympy/sympy/issues/10688)

[#10713](https://github.com/sympy/sympy/pull/10713): Proposing a method to get general form for list of args.

[#10733](https://github.com/sympy/sympy/pull/10733): Rewriting [#10552](https://github.com/sympy/sympy/pull/10552) and [#10482](https://github.com/sympy/sympy/pull/10482) with extensions. Fixes [#10671](https://github.com/sympy/sympy/issues/10671) , [#7914](https://github.com/sympy/sympy/issues/7914) , [#9531](https://github.com/sympy/sympy/issues/9531) , [#9606](https://github.com/sympy/sympy/issues/9606) , [#9824](https://github.com/sympy/sympy/issues/9824) , [#10426](https://github.com/sympy/sympy/issues/10426) , [#10217](https://github.com/sympy/sympy/issues/10217) and most of the XFAIL present in test_solveset.

[#10764](https://github.com/sympy/sympy/pull/10764): TODO part of [#10733](https://github.com/sympy/sympy/pull/10733) Fixes XFAIL test-cases and [#7914](https://github.com/sympy/sympy/issues/7914)

[#10898](https://github.com/sympy/sympy/pull/10898): Implementing the logic of [#10713](https://github.com/sympy/sympy/pull/10713) in solve_trigmethod insolveset. This PR is able to give simplified solution for trigonometric equation.
Example :

```
>>>>>print solveset(cos(x) +cos(3*x) + cos(5*x), x, S.Reals)
ImageSet(Lambda(_n, _n*pi/6),Integers())

```

[#10971](https://github.com/sympy/sympy/pull/10971) Fixes [#10864]((https://github.com/sympy/sympy/issues/10864) Old solver have ` _tsolve` to solve transcendental equation, but in solveset `_invert` method can handle some works of the `_tsolve` method. One of them could be:

```
x =symbols('x' , positive = True)</span>
solveset(x**(y*z) - x,x,S.Reals)</span>
```

[#10994](https://github.com/sympy/sympy/pull/10994) Now solveset returns Integers solution for an equation using `diophantine.py` .

```
>>> solveset(2*x + 3*y - 5, x, S.Integers)
{(3⋅t₀ - 5, -2⋅t₀ + 5) | t₀ ∊ ℤ}
>> solveset(2*x + 3*y - 5, domain=S.Integers)
{(3⋅t₀="" -="" 5,="" -2⋅t₀="" +="" 5)="" |="" t₀="" ∊="" ℤ}
```

[#11008](https://github.com/sympy/sympy/pull/11008) Fixes [#10876](https://github.com/sympy/sympy/issues/10876)

### Bugs/issues reported

* [#10033](https://github.com/sympy/sympy/issues/10033) : Wrong answer by Inequality solver.
* [#10313](https://github.com/sympy/sympy/issues/10313) : Need good description about Dot printing.
* [#10453](https://github.com/sympy/sympy/issues/10453) : Integrate return wrong answer (inverse trigonometric functions).
* [#10568](https://github.com/sympy/sympy/issues/10568) : `linsolve` Returns `EmptySet` if equation is not simplified.
* [#10688](https://github.com/sympy/sympy/issues/10688) : Not able to solve some `const**(symbol)` type equation.
* [#10864](https://github.com/sympy/sympy/issues/10864) : `solveset(x**(y*z) - x, x, S.Reals)`` returns `ConditionSet`.

### Getting ready to choose a Project

As I am too much excited to work for `SymPy` all the time. Jan 2016 I started preparing the GSoC proposal. After these contribution the another major part was choosing a project and getting idea to improve certain module in `SymPy`.Then I started working on Project for the GSoC proposal.

You can read about my Project in this blog :
[GSoC 2016 Project](https://shekharrajak.github.io)
