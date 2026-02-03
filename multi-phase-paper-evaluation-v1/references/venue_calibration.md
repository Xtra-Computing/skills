# Venue Calibration Guide

This document provides venue-specific patches to adapt all phases based on target conference type.

## Core Distinction

**Systems Conferences** (OSDI, SOSP, NSDI, EuroSys, ASPLOS):
- Problem > Method > Results
- Engineering judgment and tradeoffs ARE contributions
- Prefer understated, credible, implementation-focused writing

**AI Conferences** (NeurIPS, ICML, ICLR, AAAI):
- Idea / abstraction > empirical improvement
- Conceptual novelty, formulation, generalization matter most
- Prefer conceptual, ambitious, paradigm-level writing

## Phase 0 Patches

### Systems Conference Calibration
```
When evaluating value:
- Prioritize real-world deployment pain points
- Penalize purely conceptual novelty without operational grounding
- Reward clear system bottlenecks, resource constraints, and tradeoffs
- Ask: would a systems practitioner care?
```

### AI Conference Calibration
```
When evaluating value:
- Prioritize conceptual clarity and abstraction quality
- Reward new problem formulations or unifying perspectives
- Penalize narrow, one-off system hacks
- Ask: does this change how we think?
```

## Phase 1 Patches

### Systems Conference Calibration
```
When judging story and positioning:
- Require explicit system insights (lessons learned)
- Penalize claims framed as algorithmic superiority only
- Reward articulation of tradeoffs and failure modes
- Motivation must reference realistic workloads or constraints

Quantitative motivation in systems papers:
- latency / throughput / cost / energy / failure rate
- production-scale numbers > synthetic benchmarks
```

### AI Conference Calibration
```
When judging story and positioning:
- Require a clean problem formulation
- Reward elegant problem decomposition and assumptions
- Penalize over-emphasis on implementation details
- Motivation should emphasize generality and conceptual gaps

Quantitative motivation in AI papers:
- performance gaps across tasks
- sample efficiency
- asymptotic / scaling behavior
- limits of existing paradigms
```

## Phase 2 Patches

### Systems Conference Calibration
```
When evaluating structure:
- Ensure system overview appears early
- Require explicit sections on design decisions and tradeoffs
- Penalize long theoretical buildup before system intuition
- Paragraphs should answer: what did we build and why?
```

### AI Conference Calibration
```
When evaluating structure:
- Ensure problem definition and formulation appear early
- Reward clean separation of assumptions, method, and analysis
- Penalize interleaving engineering details with core ideas
- Paragraphs should answer: what is the idea and why does it work?
```

## Phase 3 Patches

### Systems Conference Calibration
```
When evaluating writing style:
- Prefer precise, understated, engineering-style language
- Penalize hype, grand claims, and vague generalization
- Figures should emphasize system architecture, workflows, and bottlenecks
- Tables should expose tradeoffs, not just best numbers
```

### AI Conference Calibration
```
When evaluating writing style:
- Prefer clarity, abstraction, and conceptual signposting
- Reward intuitive explanations and clean visualizations
- Penalize excessive implementation detail
- Figures should convey ideas, trends, and generalization behavior
```

## Application Instructions

1. Identify target venue type at the start
2. Load appropriate patches into each phase
3. Apply patches as ADDITIONAL criteria, not replacements
4. When in doubt, default to the venue's acceptance prior

## Venue Type Detection

If venue not explicitly specified, infer from:
- Paper content: Systems-heavy → Systems, Algorithm/theory-heavy → AI
- Author affiliation: Systems lab → Systems, ML lab → AI
- Cited work: Mostly systems papers → Systems, Mostly ML papers → AI

## Multi-Venue Submissions

When targeting both:
1. Run both calibrations
2. Identify conflicts
3. Choose the MORE CONSERVATIVE stance (harder gate)
4. Recommend venue preference to author
