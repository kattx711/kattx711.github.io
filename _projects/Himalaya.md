---
layout: page
title: Himalayan Uplift
description: Kinematic dislocation model to vertical uplift in the Himalayas
importance: 13
category: project
giscus_comments: false
---

One can infer vertical uplift from the elastic dislocation model for a thrust fault. I'm using solutions from Chapter 3 of *Earthquake and Volcano Deformation* by Paul Segall (2010).

## Equation (3.70): Surface displacements (buried semi-infinite fault)

This equation calculates the surface displacement from a single, buried edge dislocation whose top is at depth *d*.

$$
\begin{aligned}
u_1(x_1, x_2 = 0) &= \frac{s}{\pi}\Big[ \cos\delta \tan^{-1}(\zeta) + \frac{\sin\delta - \zeta\cos\delta}{1+\zeta^2} \Big], \\
u_2(x_1, x_2 = 0) &= -\frac{s}{\pi}\Big[ \sin\delta \tan^{-1}(\zeta) + \frac{\cos\delta + \zeta\sin\delta}{1+\zeta^2} \Big],
\end{aligned}
$$

It seems clear that in the Himalayas, there is a flat–ramp–flat structure, and the ramp is locked during the interseismic period (Cattin & Avouac, 2000). The lower flat creeps steadily at known rates (~20 mm/yr). Suppose the upper flat and ramp remain locked indefinitely—then the interseismic uplift equals the “long-term uplift,” which may persist as signals in bedrock river profiles. In contrast, if the entire flat–ramp–flat system slips at the same rate over a sufficiently long observation window, the system is at steady state. Between these two endmembers, the intensity and location of maximum uplift will shift due to the varying contributions of each fault segment. Therefore, fitting the river’s bulge position to this gradient could quantify the degree of imbalance. A strong prior, I think, is that this fraction cannot be 0 (no slip on the flat and ramp) or 1 (because Himalayan coseismic ruptures are highly irregular and separated by long intervals).

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="/assets/img/rampislocked/rampislocked.gif" title="Evolution of Uplift" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
