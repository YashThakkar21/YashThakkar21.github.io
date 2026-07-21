---
layout: page
title: A Smarter Search for Tree of Thoughts
description: Replacing Tree-of-Thoughts' BFS/DFS with A* and MCTS — and finding that evaluator calibration, not search, is the bottleneck.
permalink: /projects/tree-of-thoughts-search/
importance: 2
category: research
github: https://github.com/YashThakkar21/smarter-search-for-tree-of-thoughts
paper: https://drive.google.com/file/d/1LqR2tY1I4ndmFvawkI0gjoOPjsv9bUo7/view?usp=sharing
---

**Python · GPT-4 API** — Spring 2026 · [Code]({{ page.github }}) · [Paper]({{ page.paper }})

Tree of Thoughts (ToT) improves LLM reasoning by exploring a tree of intermediate steps rather than committing to one chain — but the original formulation searches that tree with plain BFS or DFS. Both are uninformed: they expand nodes without using what the model already knows about which branches look promising. We asked whether informed search does better.

### What we changed

- **A\* with a lazy LLM-scored heuristic.** Rather than scoring every frontier node, the heuristic is evaluated on demand, since each call is an expensive LLM query. Node cost combines depth with the model's own estimate of how close a partial solution is to complete.
- **MCTS with UCT exploration.** Rollouts balance exploiting high-value branches against exploring under-visited ones, with the LLM acting as the value estimator at leaf nodes.

Both were benchmarked against BFS/DFS baselines on Game of 24 and crossword tasks.

### The finding

**Search gains are bounded by evaluator calibration.** MCTS beat BFS only when the LLM's state evaluations were reliable; where the evaluator was poorly calibrated, smarter search amplified its errors — confidently exploring branches that scored well and led nowhere. The bottleneck in ToT-style reasoning is not the search algorithm but the quality of the value signal it searches over.
