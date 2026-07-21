---
layout: page
title: Semantic Reasoning Evaluation in LLMs
description: Does Qwen2.5-Coder actually reason about code semantics, or exploit surface cues? Identifier obfuscation says it's some of both.
permalink: /projects/llm-semantic-reasoning/
importance: 3
category: research
github: https://github.com/YashThakkar21/llm-semantic-reasoning-evaluation
paper: https://drive.google.com/file/d/1Dv7dyQ8Gn4GhO2I7vKpTKfy15nOibzOd/view?usp=sharing
---

**PyTorch · Qwen2.5-Coder-32B · HuggingFace** — Fall 2025 · [Code]({{ page.github }}) · [Paper]({{ page.paper }})

When a code model correctly summarizes a function named `binary_search`, we can't tell whether it traced the logic or read the name. This project separates the two by systematically stripping away surface cues and measuring what survives.

### Method

- **Synthetic dataset generation.** Programs were generated with controlled structure so that semantics could be held fixed while surface form varied.
- **Identifier obfuscation ablations.** Function and variable names were replaced with semantically empty tokens, removing the naming shortcut while leaving behavior unchanged.
- **Error-detection ablations.** Deliberate bugs were injected at known positions to test whether the model could localize a fault rather than merely flag that something was wrong.
- **LLM-as-a-judge.** A separate model scored output equivalence, allowing evaluation of free-form explanations that exact-match metrics cannot handle.

### The finding

The model **preserves intent under obfuscation** — it still describes what obfuscated code does, so its understanding is not purely lexical. But it **fails at multi-step error localization**: as the number of reasoning steps between the bug and its observable effect grows, accuracy degrades sharply. The model knows what code *means* better than it can trace how that meaning breaks.
