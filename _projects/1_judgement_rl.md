---
layout: page
title: Multi-Agent RL for Imperfect-Information Games
description: Self-play PPO agents that learn to bid and play Judgment from raw game states — and beat experienced humans.
permalink: /projects/judgement-rl/
importance: 1
category: research
github: https://github.com/YashThakkar21/judgement-rl
paper: https://drive.google.com/file/d/1xBYyfL6GBJPuadDg3msNEah1upDYd1tP/view?usp=sharing
---

**Python · PyTorch · PPO** — Spring 2026 · [Code]({{ page.github }}) · [Paper]({{ page.paper }})

Judgment is a trick-taking card game where each player first *bids* the exact number of tricks they expect to win, then plays to hit that number precisely. Overshooting is punished as harshly as undershooting, and you can never see anyone else's hand. That makes it a clean testbed for decision-making under partial observability: the bid commits you to a target before you have the information needed to evaluate it.

### Approach

- **Multi-agent self-play loop.** Agents train against continuously updated copies of themselves, so the strategy landscape shifts as they improve rather than converging against a fixed opponent.
- **PPO with action masking.** The legal action set changes every trick — suit-following rules, cards already played, bids already claimed. Masking invalid actions before the policy softmax keeps gradient signal from leaking into moves that can never be taken.
- **Belief-state features.** Rather than feeding the network only the visible table, the observation includes derived beliefs about what opponents likely hold, inferred from bidding behavior and cards played so far.

### Results

The trained agents surpassed experienced human players. More interestingly, they developed **emergent bidding strategies** that were never hand-coded — including deliberately conservative bids from weak hands to sabotage opponents' targets, a tactic strong human players use but which the agents discovered directly from raw game states.
