---
title: "Dirt simple DE"
created_at: 2016-08-09T20:52:57-07:00
kind: article
---

I'm working through the exercises of a dynamics textbook for lack of worse things to do.

Dynamics is pretty neat. It is a part of mathematics useful for modeling approximately continuous physical processes. This is analogous to computers, which are useful for modeling discontinuous processes. (I'm going to write about that analogy later, but it's a subject that requires a lot of precision.) If you're used to computer models, which tend to be lengthy series of pretty opaque numeric operations possibly written in some obscure language like IDL, the seeming terseness of most dynamic models can be a bit surprising. Where do all these constants come from? How can you draw important conclusions without even having values?

Well, that's what I thought when I began learning dynamics, anyway. As it turns out, this is how it works because it's pretty easy to invent a dynamic model, and easy to describe, and in some cases determine, their qualitative behavior.

<!-- more -->

What is dynamics?
-----------------

Dynamics was invented by Newton*. He wanted to know how physical objects, like planets, move. Naturally this means you want to think about the positions of planets. Pretty obviously you might also be concerned with their velocity, that is the _rate_ at which their positions change, and maybe even their acceleration, the _rate_ at which their velocities change. Not infrequently, velocities and acclerations depend on positions, and so on. Newton's law of gravitation, for example, tells you that the acceleration due to gravity of an object depends on the inverse square of its distance (relative position) to whatever object is exerting a gravitational pull. You can write this down something like

d²r/dt² = k/r²

which is to say, the rate of the rate of change of r equals k (a constant of proportionality) times the inverse square of r. This equation is called a "differential equation" because it relates a quantity (position) to its rates of change, or "derivatives" (d²r/dt²).

This is dynamics. You have rates of change for one or more variables in terms of those variables, and you want to know how those variables actually change - the actual path of the planet, or whatever. Those variables are functions of one independent variable, usually "time": r(t) = something. (Multiple independent variables takes you to partial differential equations, which are rather more complicated.)

Basic population growth
-----------------------

Every text on dynamics starts with modeling population growth. If you understand this you can skip the first lecture of any class on the subject.

Say you want to know how the population of an animal species changes over time. You could spend fifty years trapping hares to get samples of the total population, or if you have a reliable human census, use that. In either case you get _specifics_. If a meteor struck and killed large parts of the population in the period your data covers, you're going to see unusual population changes and it's going to be difficult to extrapolate the future unless you drop a meteor later yourself. You need some kind of theory to explain the numbers you see.

And hey, trapping is hard, so why not just start there?

You simplify things greatly. Say you only want to deal with one variable, the population itself. Famines and wars and such are right out. So you might write out

dP/dt = f(P)

which is to say that the rate that P, the population, changes, is some arbitrary function of only P itself.

That's too vague to solve. You must make further simplifications. You can suppose then that the function f is linear. So, for instance, if you have two populations, and one is twice as large as the other, you would suppose that the larger population grows twice as fast, because there are about twice as many animals/couples reproducing.

You can also suppose that f(0) = 0, i.e. that if everybody is dead they will not be coming back. Sad!

These two assumptions together reduce f to being a multiplication by a constant, so your population growth equation is

dP/dt = cP

Behold. A model. You can get a curve out of this, P(t) = P(0)exp(ct), and graph it and watch population grow. Regardless of what c or P(0), you will note that P "accelerates", and grows faster as it grows (as expected from our equation). This is "exponential growth".

It's simple, very super simple, but it's enough of a model that you can derive some interesting things like Maltusian catastrophes or [Marxism](http://stochastictalk.blogspot.com/2016/05/karl-marx-at-sunset-of-classical.html) with some more work.

Of course, you also just made it up, so probably do some empirical validation before you start crowing about surplus population and well yeah.

Carrying capacity
-----------------

Now let's say you do some empirical work, maybe go out and work for Hudson's Bay Company but don't make enough money on hare furs to quit your modeling job, so you go back to the grindstone.

In your observations you've noticed that the environments populations of animals live in have what you call a "carrying capacity". If the population in an area is above this "capacity" level, there is not enough food, space for burrows, whatever, and the population dies off. Below the carrying capacity, the population does still grow, but it slows down as it approaches the capacity. You want to modify the above population growth equation with this capacity, call it a constant, K                             .

You want positive growth P < K and negative growth (death) for P > K. Negative growth just means dP/dt is negative, so one way to do this would be to multiply the existing equation by a number that's negative only when P > K:

dP/dt = cP(K - P)

This sort of works, but has the odd consequence that the growth rate can depend pretty directly on the value of K. E.g., a very low (i.e., the limit as P goes to zero) population in an environment with a K of 10000 will grow about a hundred times faster than one in an environment with a K of 100. This doesn't exactly fit our ideas of how populations grow, since that higher K could just mean, say, a hundred times more area, for a species that doesn't even travel around that much.

Maybe what we want to say is that as K increases to infinity, we recover the original simple dP/dt = cP. Having new models be conservative extensions to existing ones is a useful tactic.

So instead we can work with the ratio, P/K. P/K is greater than one when P > K, and less than one when P < K, so:

dP/dt = cP(1 - P/K)

and when K approaches infinity (or as P approaches zero), the parenthetical term approaches 1, giving us back our original model.

"Explicit" solutions
--------------------

New model, great. Can we write out an equation to graph, like we did for dP/dt = cP? It turns out that we're out of luck there, but that may not be so bad.

You can "explicitly" "solve" any one dimensional differential equation by separation of variables. The solution of dy/dx = F(y) is

![one-dimensional DE solution](https://wikimedia.org/api/rest_v1/media/math/render/svg/689ac8cba86b425a32c080e57727b90611f8068b)

That is, you can find x as a function of y, but not y as a function of x, at least immediately. It's a bit odd. If you include y(0) as the bottom limit of integration, you can find x(t) and eliminate the integration constant.

For the original dP/dt = cP, for instance, we'd integrate 1/(cP), giving us t(P) = log(P(t))/c - log(P(0))/c. Do some algebra and you'll see that this implies log(P(t)) = ct + log(P(0)); exponentiate both sides and P(t) = P(0)exp(ct) as previously mentioned.

Inverting the function of time cannot always be done. If we had dx/dt = -x/(1+x²), for instance, we would find that "explicitly", log(x) + (1/2)x² = -t + log(x(0)) + (1/2)(x(0))², and good luck with that. And of course, sometimes the antiderivative might not be expressible in elementary functions to begin with.

But that's not so important, because given just the differential equation(s), you can solve "by quadratures", also known as "by numerical integration". This is quite a common thing to do, and hey, if you're graphing an exponential function on your computer it's probably doing _something_ iteratively.

The interesting thing here is that dynamic models can very easily, or even often, result in unfamiliar functions.

Land use
--------

Now let's really complicate this model. The following is a set of equations from [Dobson, Bradshaw, and Baker 1997](http://dx.doi.org/10.1126/science.277.5325.515).

Let's restrict to humans, and say we want to do this for a specific reason: we're concerned about farming ecology (e.g. slash-and-burn is a big issue in South America, etc.). So we add a variable, A, to represent the agricultural land area. We further assume that the carrying capacity is proportional to A (i.e. twice as much farmland = twice as much capacity), so

dP/dt = cP(1-P/(hA))

The amount of farmland fluctuates as well. To model land use, we divide all land up into three kinds: farmland (A), forest (F), and unused or "other" (U). Farmland can be increased by people converting unused land or forest into farms, and decreased by farms being abandoned or the land being overused. We make up some constants, and

dA/dt = dPF + bU - aA

The term for converting forests involves an additional factor for the population - people will be more motivated to burn down forest for land when they need more food. You could put that factor on the conversion from unused land as well, but it's nice to reduce the number of nonlinear terms, and ecologists are presumably more preoccupied with forests.

Forest grows over unused land. Call the constant for that s, and you get two more equations for area changes:

dF/dt = sU - dPF
dU/dt = aA - (b+s)U

So we have four differential equations total, which are all linked.

An important thing to note is that the total land, P+A+F, is conserved. Which makes sense, you can't just make more land. You can observe this is true in the model by seeing that d(P+A+F)/dt = dP/dt + dA/dt + dF/dt = 0.

Long term behavior
------------------

Earlier I mentioned that exponential growth, well, grows. This is obviously not true of every dynamical system, but there are only so many ways a dynamic system can "end" - only so many things an f(t) can be as t goes to infinity.

Firstly it can approach a constant (which may be infinity). This happens with normal exponential growth if P(0) = 0; P(t) = 0 forever, because no more population is going to be created from nothing. It also happens, a bit more subtly, in the carrying capacity version; if P/K = 1 (so P = K), dP/dt equals zero, so P just stays there. This is called an equilibrium state.

You find an equilibrium state by setting all the rates of change to zero, so that nothing moves. This may be easier said than done, for complicated systems, but it's workable for the land use thing here.

dP/dt = 0 = cP(1-P/(hA)), so either P = 0 or P = hA. For P = 0, dF/dt = 0 = sU - dPF shows that sU = dPF, but P = 0, so U = 0. dA/dt = 0 = dPF + bU - aA then shows A is zero as well, and F is unconstrained; so everybody being dead and all the world (however large it is) being forest is an equilibrium. If P = hA, sU = dPF = dhAF. From dU/dt, aA = (b+s)U, and substituting back sU = dh(1/a)(b+s)UF, so F = as/(dh(b+s)); the other values can be worked out similarly. So there are two equilibria.

There could additionally be cycles, some set of values that repeatedly evolves back to itself. These are much harder to find, especially in higher dimensions; I vaguely remember a story about a Russian mathematics professor passing out to each of his students a random quadratic DE systems and telling them to find any limit cycles, and getting no results.

And since it's (bigger than) three dimensional, it can additionally have toruses, and strange attractors, and all that.

But at least we got a model.

\*: Leibniz invented calculus independently, but I don't know what he used it for. There's a lot of important work Newton and Leibniz could use to build calculus, like Fermat's (of theorem fame) adequality. Newton, however, built a whole theory of differential equations (or "fluxions"), so I'm blaming him. They were all hella smart dudes regardless.
