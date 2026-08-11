# Prompts

This directory contains the prompts used in the experimental study of collaborative cyber threat analysis based on a Semantic Digital Twin.

The prompts implement three experimental modes designed to compare different approaches to organizing analytical reasoning and knowledge exchange while keeping the initial network model, OSINT/RAG context, threat topic, and analytical task equivalent.

## Experimental Modes

### 1. Single LLM

**File:** `single-llm-prompt.txt`

Baseline experimental mode in which a single Large Language Model analyzes the network model and the retrieved OSINT context and produces the complete analytical result.

No explicit multi-agent decomposition or shared Semantic Digital Twin is used.

This mode provides the baseline for evaluating the effect of agent specialization and structured knowledge sharing.

---

### 2. Multi-Agent Textual Collaboration

**File:** `multi-agent-text-prompt.txt`

The analytical task is distributed among specialized AI agents responsible for network analysis, vulnerabilities, TTPs, source provenance, attack scenarios, attribution, contradictions, and other analytical functions.

Agents exchange their intermediate results through textual representations, and a moderator integrates them into the final analytical report.

No persistent shared machine-interpretable semantic state is maintained between agents.

This mode is used to evaluate the effect of functional agent specialization independently of the Semantic Digital Twin.

---

### 3. Multi-Agent Collaboration through Semantic Digital Twin

**File:** `semantic-digital-twin-agentflow-prompt.txt`

This is the proposed experimental mode.

Specialized agents collaborate through a shared **Semantic Digital Twin (SDT)** rather than relying primarily on textual message exchange.

Each agent:

1. reads the current SDT state;
2. performs its specialized analytical function;
3. proposes a structured change;
4. associates the change with evidence, provenance, confidence, and epistemic status;
5. submits the change to the moderator;
6. receives the validated shared SDT state during subsequent analytical stages.

The Semantic Digital Twin therefore acts simultaneously as:

- a formal representation of the investigated cyber situation;
- shared analytical memory;
- a machine-interpretable knowledge space;
- an evidence-bearing semantic graph;
- a substrate for collaborative multi-agent reasoning;
- a source for attack, attribution, and response scenarios.

The prompt is implemented using structured **AgentFlow natural-language pseudocode**.

---

## Common Experimental Inputs

All three experimental modes use equivalent initial inputs:

- the same corporate network model;
- the same OSINT/RAG corpus;
- the same cybersecurity problem (`THREAT_TOPIC`);
- the same underlying LLM where possible;
- the same general analytical objectives.

The investigated threat topic used in the current experiment is:

> **Email-based social engineering leading to credential compromise, privilege escalation, and lateral movement in a Windows domain network.**

This design makes it possible to investigate the effect of the **knowledge-sharing mechanism** rather than differences in input data or analytical objectives.

---

## Experimental Repetition

Each experimental mode is executed **five times** under equivalent initial conditions.

The resulting outputs are evaluated using the following metrics:

- Completeness;
- Consistency;
- Traceability;
- Contradiction Detection;
- Scenario Coverage;
- Attribution Stability.

The comparison is intended to determine whether the transition from a single LLM and textual multi-agent communication to collaboration through a shared Semantic Digital Twin improves the structural quality, traceability, and reproducibility of cyber threat analysis.

---

## Files

```text
prompts/
├── README.md
├── single-llm-prompt.txt
├── multi-agent-text-prompt.txt
└── semantic-digital-twin-agentflow-prompt.txt
