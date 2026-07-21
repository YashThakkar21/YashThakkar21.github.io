---
layout: page
title: Pedestrian Detection Benchmark
description: HOG, CNN, ViT, and SAM2 on the same pedestrian dataset — what forty years of computer vision buys you, and what it costs.
permalink: /projects/pedestrian-detection/
importance: 5
category: research
github: https://github.com/s-bhatia1216/pedestrian-detection
paper: https://drive.google.com/file/d/1ARuDzLRI2P5gvrx-hfGsxX9vOVDj-0Ht/view?usp=sharing
---

**Python · PyTorch** — Fall 2025 · [Code]({{ page.github }}) · [Paper]({{ page.paper }})

Pedestrian detection has a long history, and each era left behind a different approach: hand-engineered gradient features, convolutional networks, vision transformers, and now promptable foundation models. They are rarely measured against each other under identical conditions.

We benchmarked four pipelines — **HOG**, **CNN**, **ViT**, and **SAM2** — on the PnPLO pedestrian dataset, holding the data, splits, and evaluation protocol fixed across all of them.

### What the comparison shows

The headline is the **accuracy-latency tradeoff**, not accuracy alone. Foundation-model pipelines lead on detection quality, particularly on occluded and small-scale pedestrians where classical features degrade badly. But they pay for it in inference cost by orders of magnitude — which is exactly the constraint that matters for the embedded, real-time settings where pedestrian detection is actually deployed. HOG remains competitive on clean, well-lit, unoccluded instances at a fraction of the compute.
