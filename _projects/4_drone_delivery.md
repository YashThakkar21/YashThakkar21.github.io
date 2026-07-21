---
layout: page
title: Low-Cost Drone Delivery Platform
description: An open-source autonomous payload-drop system for commodity drones — 7 design iterations to 80% in-flight release reliability.
permalink: /projects/drone-delivery/
importance: 4
category: systems
github: https://github.com/YashThakkar21/low-cost-drone-delivery-platform
paper: https://drive.google.com/file/d/1xV5i5eZY8M6mFdPZU48OJArCQH-7nCON/view?usp=sharing
---

**C++ · Arduino · CAD** — Spring 2026 · [Code]({{ page.github }}) · [Paper]({{ page.paper }})

Commercial drone delivery hardware is expensive and closed. This project builds an autonomous payload-drop system out of commodity parts — an Arduino, an ultrasonic rangefinder, and 3D-printed mechanisms — that any hobbyist drone can carry.

### System

- **Ultrasonic ground detection** triggers release at a target altitude above ground rather than at a fixed GPS altitude, which matters over uneven terrain.
- **3D-printed release mechanism** designed in CAD, with the full parts library published so the build is reproducible.
- **Embedded C++ control loop** on Arduino handling sensor filtering and actuation timing.

### Iteration

The interesting part was the failure analysis. Across **7 design revisions**, each failure mode — servo torque under payload load, sensor noise from rotor downwash, mechanical binding at release — drove a specific change to the next revision. The final design reached **84% bench** and **80% in-flight** release reliability, with the gap between the two traced primarily to vibration-induced sensor noise that does not appear on a static bench.
