---
name: multi-phase-paper-evaluation-v1
description: Multi-phase agentic academic paper evaluation and improvement system. Use when users want to systematically evaluate, refine, or improve academic papers through rigorous multi-agent review spanning research value assessment, story/positioning, structure, and writing quality. Supports both systems and AI conference styles with venue-specific taste calibration.
---

# Paper Review System

A comprehensive multi-phase agentic system for evaluating and improving academic papers with senior researcher-level rigor.

## System Architecture

This system operates through **4 mandatory phases** with strict gate controls:

- **Phase 0**: Strategic Value & Venue Fit
- **Phase 1**: Story, Positioning & Claims  
- **Phase 2**: Structure & Subsections
- **Phase 3**: Paragraphs, Figures & Camera-Ready

Each phase must **PASS** before advancing. Failed phases trigger targeted iteration until quality thresholds are met.

## Core Philosophy

**This is NOT a text editor.** This system:

- Simulates senior PI + program committee decision-making
- Applies venue-specific research taste and acceptance priors
- Enforces iterative quality control with rollback capability
- Optimizes for acceptance likelihood, not just clarity

## Usage Workflow

### 1. Configure Venue Profile

First, specify the target venue to calibrate all agents:

```
Venue type: [Systems / AI]
Target conference: [e.g., OSDI, NeurIPS, ICML]
```

Load venue-specific calibration from `references/venue_calibration.md`.

### 2. Execute Phase Sequence

Run phases in strict order with mandatory gates:

#### Phase 0: Value & Venue Fit
- **Purpose**: Determine if the paper is worth pursuing
- **Prompt**: `references/phase0_value_venue_gate.md`
- **Agents**: 10 roles (Problem Value, Research Taste, Venue Fit, etc.)
- **Gate**: PASS only if problem valuable AND venue-appropriate

#### Phase 1: Story & Positioning
- **Purpose**: Ensure acceptance-ready story and claims
- **Prompt**: `references/phase1_story_positioning.md`
- **Agents**: 11 roles (Motivation, Novelty, Positioning, etc.)
- **Gate**: PASS only if claims defensible AND motivation convincing

#### Phase 2: Structure & Subsections
- **Purpose**: Optimize logical flow and reader guidance
- **Prompt**: `references/phase2_structure.md`
- **Agents**: 11 roles (Structure Architect, Paragraph Focus, etc.)
- **Gate**: PASS only if structure serves story with minimal redundancy

#### Phase 3: Camera-Ready Polish
- **Purpose**: Achieve submission-ready presentation quality
- **Prompt**: `references/phase3_camera_ready.md`
- **Agents**: 14 roles (Paragraph Intent, Figure Design, Style, etc.)
- **Gate**: PASS only if submission-ready for target venue

### 3. Iteration Control

When any phase returns **FAIL**:

1. Extract specific deficiencies from agent reports
2. Identify rollback scope (claim / section / paragraph level)
3. Re-run only necessary agents
4. Track iteration count and acceptance likelihood trend
5. Continue until PASS or diminishing returns detected

### 4. Orchestration

Use `references/orchestrator.md` for the master control prompt that:
- Manages phase sequencing
- Enforces gate decisions
- Handles iteration loops
- Tracks quality trajectory

## Key Design Principles

1. **Value before story** - Don't optimize what shouldn't exist (Phase 0)
2. **Multi-perspective rigor** - 8-14 independent agents per phase
3. **Explicit quality control** - Anti-BS agents in every phase
4. **Taste-driven decisions** - Research taste explicitly modeled
5. **Venue calibration** - Systems vs AI conference taste differences
6. **Iterative refinement** - Mandatory loops with rollback

## Output Format

Each phase produces:

```
[Phase X Result]
Gate: PASS / FAIL

P0 Issues (must fix):
- Issue: [description]
- Evidence: [location in draft]
- Fix: [concrete action]
- Expected impact: [improvement]
- Verification: [how to check]

P1 Issues (should fix): ...
P2 Suggestions (nice to have): ...

Author Action Plan (ordered checklist):
1) [specific edit with location]
2) ...

Reviewer Simulation (after fixes):
- Reviewer A: [verdict + reasoning]
- Reviewer B: [verdict + reasoning]
- PC Chair: [verdict + reasoning]
```

## Compile the ourput into one report

Compile the output into one report.

## When to Use This System

Trigger this skill when users:
- Want comprehensive paper evaluation beyond grammar
- Need strategic guidance on research direction
- Seek acceptance-oriented improvement  
- Request venue-specific optimization (systems vs AI)
- Ask for multi-phase systematic review
- Need research taste / quality assessment

## Resources

- `orchestrator.md` - Master control system

### references/
Complete phase-specific prompts ready for Cursor:

- `phase0_value_venue_gate.md` - Strategic value assessment
- `phase1_story_positioning.md` - Acceptance logic
- `phase2_structure.md` - Logical flow
- `phase3_camera_ready.md` - Presentation quality
- `venue_calibration.md` - Systems vs AI conference patches

Each file contains:
- Complete agent role definitions
- Strict deliverable requirements
- Gate rules and iteration logic
- Ready to paste into Cursor

### scripts/
(Currently not needed - all agents operate via prompts)

### assets/
(Currently not needed - no templates required)