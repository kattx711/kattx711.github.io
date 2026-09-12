---
layout: page
title: Quantitative Research Internship 
description: Vega Liquidation Risk Model
img: "assets/img/clearStreet/clearstreetImg.png"
importance: 2
category: project
---

## Highlights

- Spent 10 weeks as a Quantitative Research Intern at Clear Street, developing a risk model from scratch to estimate the liquidation cost of options arising from their exposure to market volatility.
- Deployed the risk engine to production in the form of a dashboard for use by risk managers, along with a daily recalibration service for day-to-day risk re-calculations.
- Developed a cheaper approach to risk neutralization by modelling the cost of hedging exposures rather than directly liquidating the full portfolio, allowing for tighter margin estimates on institutional portfolios.
- Built the model to account for diversification benefits across portfolio holdings, provide cost attribution by risk factor, and produce estimates for both normal and stressed market regimes.

## "Options? Like... This or That?": A Problem Lost in Translation.

Okay, okay, I’ll admit that although I arrived at Clear Street with *almost* no exposure to finance, I did in fact know what an option was, thanks to that one Hedge Funds class I’d taken the previous year — that is, the right to buy the underlying asset at the time of maturity for a pre-agreed price (the strike). I guess that knowledge did help in at least giving me some sense of orientation and context, but I still felt utterly lost being handed my project spec on the first day and seeing it riddled with all this foreign language like “term structure”... and what’s with the word “shocks” being thrown around everywhere? And, most importantly, the title of my own project — vega liquidation? What is that!?

For me, the way I’ve learnt to approach any tough class at Caltech is through that careful art of a balancing act between reading enough material to acquire enough knowledge to understand what’s going on, but not getting so lost in the weeds that you paralyse yourself from just taking your own stab at it... and asking for forgiveness later!

So in my first few days, I scoured all the resources I could — textbooks, blog posts, and of course my trusty $2k-a-month Claude as well. By the end of the week, here’s what I had managed to piece together:

- From my previous knowledge, I knew that option prices are a function of many variables, one of which is volatility.
- Since we observe the others, we can infer the volatility implied by the option price — hence *implied volatility*.
- Changes in option price due to changes in volatility are captured by a sensitivity called *vega* — finally, one part of the project title down!
- If volatility moves while we’re holding a position, the option price moves too, which means that volatility exposure can make us lose money. So that’s what I need to figure out: how much money is actually at risk?

Decent start. At least now I knew what the end goal was supposed to look like: make a model that takes in a portfolio and spits out a vega liquidation cost.

Okay... but how do I actually sit down and calculate that? Would I really have to go through every ticker, record all of its historical volatility movements, and somehow model each one separately? The dimension of the problem blows up really fast...

One afternoon, I was feeling pretty down. I just didn’t really get what was going on. The spec kept talking about “calibrations” and “factor shocks,” and I still didn’t understand how any of those tied back into the end goal.

So I turned to Claude and prompted:

*“Explain the idea of this project to me like I’m an undergrad physicist with no market knowledge.”*

And it tells me something along the lines of:

*“At a given point in time, every option is characterized by quantities such as delta and time to expiry. Consider the implied volatility surface in this space. Our goal is to model the movements of implied volatility at every point on that surface. We can model those movements by breaking them down into global normal modes of the volatility surface — such as a level shift, changes in skew, curvature moves, and so on. Every local movement of the surface can therefore be represented as a combination of those fundamental modes.*

*Also, by the way, the Black-Scholes equation is basically the heat equation under a change of variables, and its solution comes from the same kind of machinery you’d use to solve a PDE with a Green’s function.”*

“Ohhh...! Why didn’t you just say that from the start...”

So all this risk really comes down to the same kind of ideas as modelling the movement of a taut surface after it’s been plucked — a much more familiar setting to a physicist — except here the thing moving is the implied volatility surface.

And what’s more, in the same way that we can project a movement onto normal modes and describe how much of each component it contains, we can take the analogy even further. We can actually neutralize our risk using the same idea by constructing option strategies that behave like eigenvectors of those modes — strategies exposed primarily to one fundamental type of movement — and use them to hedge or offset our existing exposure.

That analogy is what finally made everything click for me. There was still a lot to refine from that very vague picture into the actual markets and vega liquidation problem, but this was the tether I needed to finally feel like I could make principled headway in my implementation and understand what the spec was actually saying.

The “factor shocks” were exactly the movements of the volatility surface broken down into those factors, or normal modes. And the “calibration” was simply figuring out how large those movements tended to be over a given time horizon for a particular ticker or fine cluster of “similar” options — in other words, using historical data to estimate a sensible proxy for the day-to-day movements in implied volatility that we might expect.

It wasn’t all smooth sailing after this enlightenment. I scrapped my implementation at least twice before I finally got the full hindsight view of how the pieces of the engineering puzzle should fit together — fetching the data from the database, processing it, and feeding it into the risk engine in a modular way that cleanly separated the data-fetching side from the analytical algorithm itself. But this was definitely the turning point when I finally got a full conceptual understanding of what the whole problem was really about.

That afternoon, I still came away frustrated... but now for a completely different reason: physics and finance really do have so many of the same ideas, and what a shame it is that quants don’t speak the same language as physicists! But maybe they’re not two foreign languages altogether. More like regional dialects.

So if you’re ever having a hard time grasping an idea, maybe it’s not the idea itself that’s difficult — maybe it’s just what’s getting lost in translation.