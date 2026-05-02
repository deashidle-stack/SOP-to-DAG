---
title: research-summary
type: note
permalink: personal/skills/sop-to-dag/references/research-summary
---

# Research Foundation

## SOPStruct (Garg et al., JP Morgan AI Research, March 2025)
**Paper:** "Generating Structured Plan Representation of Procedures with LLMs" (arXiv:2504.00029)

Three-phase pipeline: Segment → Structure → Aggregate
- Converts unstructured SOPs into DAG representations
- Node schema: name, description, dependencies, inputs, inputs_from_deps, outputs, category
- Categories: Human Input, Information Processing, Information Extraction, Knowledge, Decision
- Evaluation: 100% on Structured Plan Score, Dependency Score, Input-from-Dependency Score across 3 datasets
- Datasets tested: Nestful API (simple), RecipeNLG (medium), Business Process (complex)
- Outperforms zero-shot, code-style, and BPMN generation methods

## PDDL Validation (from SOPStruct)
Deterministic validation using Planning Domain Definition Language concepts:
- **Predicates:** available(?v), required-input(?v, ?s), subtask-output(?v, ?s), map(?v1, ?v2)
- **Actions:** execute-subtask(?s), assign(?v1, ?v2)
- **Validation:** If a PDDL planner finds a valid plan traversing the DAG, the graph is structurally sound

## Flow-of-Action (2502.08224, early 2026)
SOP-guided agents improve root cause analysis accuracy from 35.5% → 64.01% (near-doubling).
Key insight: explicit control-flow constraints on tool invocation reduce hallucination.

## SOP-Maze (2510.08942, late 2025)
Benchmark: 397 business-realistic tasks with branching SOPs.
Finding: Even top LLMs max at ~46% accuracy on complex branching SOPs.
Implication: Structured representation is load-bearing, not a nice-to-have.

## Agent-S (2503.15520, March 2025)
Agentic workflows using SOPs as canonical guides.
Memory + fault tolerance + dynamic action selection guided by structured SOP representations.

## Key Claim (with evidence)
"No production platform converts arbitrary SOP documents into executable DAG workflows."
- SOPStruct provides academic foundation but JP Morgan has not open-sourced implementation
- Closest startups: Aident AI (instruction design), Beam AI (90%+ task accuracy), Automat ($15.5M)
- None implement the full Segment→Structure→Aggregate pipeline with PDDL validation