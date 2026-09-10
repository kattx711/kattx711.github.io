---
layout: page
title: Research at CERN
description: Search for Long-Lived Particles With HCAL Depth Segmentation
img: "assets/img/CERNImg/cover.png"
importance: 1
category: project
---

## Highlights 
- I spent my Freshman ('24) and Sophomore ('25) summers on-site at CERN in Geneva, as part of Caltech's Summer Undergraduate Research Fellowship (SURF). 
- I worked as a member of Princeton's High Energy Experiment group, led by Dr Kiley Kennedy (Princeton) and co-mentored by Professor Harvey Newman (Caltech).
- I designed and optimized various machine-learning-based classifiers for the detection of hypothesised Long-Lived Particles (LLPs). Further curiositities that spawned from this initial research question include investigating the explainability of these models, and optimizing the statistical significance of our broader analysis.
- My final research papers from my [freshman](/assets/pdf/surfFinalReport2024.pdf) and [sophomore](/assets/pdf/SURF_Final_Report_2025.pdf) summers.
- I presented a [poster](/assets/pdf/APSposterUpdated.pdf) of my work at the [APS Global Physics Summit in March 2025](https://summit.aps.org/smt/2025/events/MAR-H00/318).
- Each year, I presented my work at Caltech's Fall Seminar Day, slides [2024 slides here](/assets/pdf/CMSPresentation.pdf) and [2025 slides here](/assets/pdf/PresentationSURF2025.pdf). In 2025, I was a semifinalist in the [Doris S. Perpall SURF Speaking Competition](https://sfp.caltech.edu/undergraduate-research/communication-competitions/doris-s-perpall-surf-speaking-competition)
- Published in Caltech's [Abstract Book](https://sfp.caltech.edu/documents/29442/2024_Abstract_Book.pdf)

## How do you discover something you can't see? Trading in my senses for statistics. 

One of CERN’s ultimate goals is to discover new particles, and that’s exactly what I was working on for my two summers in Geneva. Specifically, my group and I were searching for the hypothesised Long-Lived Particle, which, as the name suggests, is a kind of particle with a lifetime greater than 0.1 nanoseconds, far longer compared to many of the Standard Model particles we know of today. For example, the Higgs decays in just 10^-22 seconds!

It’s one thing to say we’re searching for these particles, but what does that really mean? After all, how does one convince themselves, let alone the world, that we’ve really observed the existence of a new particle if we can never even hope to see one?

As humans, we’re very accustomed to relying on our five senses to navigate the world, and it’s often more than enough to just “believe it when you see it,” but that all gets rendered useless down at the subatomic scale. As I got deeper into my work, I quickly realised that to make progress I’d have to give up on these senses and start sharpening some new ones.

On the lowest level, you could say we swap our own vision for that of machines, using silicon trackers to get spatial information about charged particles, or calorimeters to measure their energy, all reconstructed into events. But even still, those are just raw events at the end of the day. How do you make sense of them?

At that stage, I learned that my best sense of direction was a combination of first principles and data (armed with NumPy and some other cute analysis tools as well). Indeed, short of climbing down into the detector itself, I had to come up with my own visual model for the process we were actually trying to study and figure out how to relate that to the event data.

The most important fact about LLPs is that because they’re delayed, they move further away from the central beam of the detector before decaying into a shower of particles, known as jets. These jets produce cone-like energy deposits as those myriads of decay products fan out. But, like the picture shown below, these delayed jets will look different from the “prompt jets” because they originate off-center, namely becoming more tightly clustered with more energy in the outer layers.

{% include figure.liquid path="assets/img/CERNImg/img1.png" class="img-fluid rounded z-depth-1" %}

And so, this mental model is exactly what pushed us toward our primary search strategy, looking at the energy deposited within the hadronic calorimeter of the detector.

When I first started out, though, I wasn’t using this mental direction to its full advantage. I was initially just working on training neural networks from lots of related features and exploring custom variables to see what the most discriminating characteristics we could find were.

But then I realised that we were sacrificing valuable information by collapsing our data into columnar form, when really one of the most important things we had to go on was the spatial information! This led us to obtain 3D “images” of these energy deposits and use them to train 3D CNNs instead, showing far more powerful and promising performance.

But the trade-off was that while we could more clearly see the intention behind the representation, the 3D CNNs themselves became more opaque. What were they actually training from? What features were they really learning?

This is how I ended up finding myself down the path of replicating the Gradient-weighted Class Activation Mapping (GradCAM) method to try and see for myself what the network was really picking up on and whether this aligned with what the theory would have us expect -- i.e., identifying LLPs by their more clustered energy deposists, thus testing how well a data-driven approach could really align with the theoretical framework.

But our lack of vision doesn’t stop there. Even with perfectly trained models, how do you go ahead and actually claim you found something statistically significant?

The way we approached it was by plotting our events in a 2D space of two assigned scores from our models, effectively interpreting them as measures of how much an event looks like an LLP event to our model. If we get hits in the top right (Signal Region), we interpret those as strongly LLP-resembling events, while the bottom left contains events that do not resemble an LLP at all.

By making finer measurements and testing the uniformity of the density of events in this 2D space, we could build a prediction for how many events we expected in our signal region and compare it with what was actually observed. In this way, we could quantify how well our prediction agreed with observation, and how statistically significant any discrepancy was, so that an excess could eventually lead us toward rejecting the null hypothesis and potentially claiming a discovery.

It’s therefore no surprise that this part of the analysis, when you finally make your prediction and compare it with observation, is known as the “unblinding” at CERN. The word almost perfectly reflects how you’ve really been in the dark this whole time, relying only on theory, mathematics, and data-science tools to make your prediction. In a way, that blindness is necessary -- it removes the temptation to bias your analysis based on how the answer “should” look and forces you to think in an entirely different way, guided not by ordinary vision but by data, systematic analysis, and math.

CERN was my first real exposure to this entirely new way of thinking, but it has set me up enormously for the work I’ve gone on to do since, learning that seeing "signal" means giving up your own senses altogether in favour of building new ones.