---
layout: page
title: Search for Long-Lived Particles With HCAL Depth Segmentation
description: 
img: "assets/img/CERNImg/cover.png"
importance: 1
category: project
---

## Overview

Over my two summers (2024 and 2025) on-site at CERN in Geneva as part of Caltech's Summer Undergraduate Research Fellowship (SURF), I worked as a researcher with the Princeton CMS group on the search for new long-lived particles (LLPs). This research is at the frontier of physics, as discovering LLPs could potentially answer fundamental questions about the universe, such as dark-matter, matter-antimatter asymetry, and supersymmetry. I have presented my work at the American Physical Society Global Physics Summit (March 2025), and at Caltech's Fall Seminar Day (2024 + 2025). I have also been selected as a Finalist in Caltech's [Perpall SURF Speaking Competition](https://sfp.caltech.edu/undergraduate-research/communication-competitions/doris-s-perpall-surf-speaking-competition).

Although LLPs do possess a distinct signature in the form of the energy deposists they leave behind within the Hadronic Calorimeter inside the Compact Muon Solenoid (CMS) detector (illustrated below), the difficulty in detecting LLPs lies in their very small theorized cross-section, making their production an extremely rare process. As a result, this analysis necessitates the [design of classifiers](https://github.com/gk199/Run3-HCAL-LLP-Analysis/tree/kat-branch/Classifiers) with a very strong background rejection power and development of [statistical frameworks for background estimation](https://github.com/kattx711/Run3-HCAL-LLP-Analysis/tree/kat-branch/FakeRate): these two areas were the subprojects that I personally led.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="/assets/img/CERNImg/img1.png" class="img-fluid rounded z-depth-1" %}
  </div>
</div>


<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    {% include figure.liquid path="/assets/img/CERNImg/img2.png" class="img-fluid rounded z-depth-1" %}
    <p class="mt-2">
      <em>A panel of plots showing the proportion of signal and background events selected after applying a given cut threshold. This illustrates the trade-off between applying too low of a threshold — while much of the signal is selected, little background is rejected. If the threshold is too high, then not enough signal is retained and the statistical significance (effectively the signal-to-noise ratio) depletes. Thus, we search for the non-trivial threshold that maximises the statistical significance for our data.</em>
    </p>
  </div>
</div>

### Key Links:

* [Interim reports](https://github.com/kattx711/Run3-HCAL-LLP-Analysis/blob/main/SURF_Interim_Report_2025.pdf) and [final research papers](https://github.com/kattx711/Run3-HCAL-LLP-Analysis/blob/main/SURF_FinalReport2024.pdf) containing detailed accounts of my personal work and findings
* [Poster](https://github.com/kattx711/Run3-HCAL-LLP-Analysis/blob/main/APSposterUpdated.pdf) presented at the APS Global Physics Summit Conference and the [description](https://summit.aps.org/smt/2025/events/MAR-H00/318)
* [Presentation slides](https://github.com/kattx711/Run3-HCAL-LLP-Analysis/blob/main/CMSPresentation.pptx) given at Caltech's Fall Seminar Day and also given to the Caltech High Energy Physics Research Group
* Abstract published in Caltech's SURF [Abstract Book](https://sfp.caltech.edu/documents/29442/2024_Abstract_Book.pdf)

### Source Code:

* Link to the [main analysis repository](https://github.com/gk199/Run3-HCAL-LLP-Analysis/tree/main)
* Links to my personal contributions at [my branch](https://github.com/gk199/Run3-HCAL-LLP-Analysis/tree/kat-branch)

