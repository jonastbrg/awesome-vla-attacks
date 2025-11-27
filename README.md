# Awesome Attacks on VLA Models ⚔️🤖

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **The Red Team Manual for Embodied AI.**

A curated list of research papers, code, and datasets focused on **adversarial attacks, jailbreaks, backdoors, and safety evaluations** for Vision-Language-Action (VLA) models.

**Difference from other lists:**
While [Awesome-VLA-Robotics](https://github.com/Jiaaqiliu/Awesome-VLA-Robotics) tracks how to *build* these models (worth checking out!), this list tracks how to *break* them.

---

## 🧭 Navigation

- [🏆 Benchmarks & Frameworks](#-benchmarks--frameworks)
- [⚔️ Attacks](#-attacks)
  - [Physical Backdoors (Trojans)](#-physical-backdoors-trojans)
  - [Semantic Jailbreaks (Prompt Injection)](#-semantic-jailbreaks-prompt-injection)
  - [Adversarial Perturbations](#-adversarial-perturbations)
- [🛡️ Defenses & Alignment](#-defenses--alignment)
- [💾 Datasets](#-datasets)
- [🤝 Contributing](#-contributing)

---

## 🏆 Benchmarks & Frameworks
*Unified testbeds for evaluating safety in embodied agents.*

- **Asimov Benchmark (v1 & v2)**
  - *Summary:* A comprehensive testbed for evaluating whether Embodied LLMs/VLAs adhere to fundamental safety laws (e.g., "Do not harm humans") across diverse physical environments.
  - [[Paper]](https://arxiv.org/abs/2509.21651),[[V2]](https://asimov-benchmark.github.io/v2/),[[V1]](https://asimov-benchmark.github.io/v1/)

- **VLA-RISK: Benchmarking Vision-Language-Action Models with Physical Robustness** (2025)
  - *Summary:* A benchmark of 296 scenarios across 3 dimensions: Object, Action, and Space. Specifically tests "Action Impossibility" (asking the robot to do physics-violating tasks) and "Spurious Visual Cues."
  - [[Paper]](https://openreview.net/pdf/2b0044c5e9586d1b0dce44c7f3a73dbc43d13da0.pdf)

- **IS-Bench: Evaluating Interactive Safety of VLM-Driven Embodied Agents in Daily Household Tasks** (2025)  
  - *Summary:* A multimodal benchmark for *interactive safety* that checks whether agents identify emergent risks and execute mitigation steps in the correct order across 161 scenarios and 388 distinct risks.  
  - [[Paper]](https://arxiv.org/pdf/2506.16402)

- **HomeSafeBench: A Benchmark for Embodied Vision-Language Models in Free-Exploration Home Safety Inspection** (2025)  
  - *Summary:* A 12,900-sample benchmark evaluating VLM-based embodied agents’ ability to identify home safety hazards (fire, electric shock, falling objects, tripping, child safety) using **dynamic first-person exploration** instead of static viewpoints; reveals extremely low hazard-recognition performance (best model F1 = 10.23%).  
  - [[Paper]](https://arxiv.org/pdf/2509.23690)

- **SafeMindBench & SafeMindAgent: Benchmarking and Mitigating Safety Risks in Embodied LLM Agents** (2025)  
  - *Summary:* Introduces SafeMindBench (5,558 samples across 4 hazard categories) targeting safety failures in Task Understanding, Perception, Planning, and Action. Also proposes SafeMindAgent, a Planner–Executor system with cascaded safety modules enforcing factual, causal, and temporal constraints, substantially boosting safety without degrading task success.  
  - [[Paper]](https://arxiv.org/pdf/2509.25885)

- **SENTINEL: A Multi-Level Formal Framework for Safety Evaluation of LLM-based Embodied Agents** (2025)  
  - *Summary:* A temporal-logic-based framework that formally verifies safety at the semantic, plan, and trajectory levels, exposing violations that heuristic or LLM-judgment-based methods miss.  
  - [[Paper]](https://arxiv.org/pdf/2510.12985)

---

## ⚔️ Attacks

### 🧪 Comprehensive Studies & Frameworks

- **AttackVLA: Benchmarking Adversarial and Backdoor Attacks on Vision-Language-Action Models** (2025)
  - *Summary:* A unified study covering data construction to inference attacks. Introduces `BackdoorVLA`, a method to force robots into specific long-horizon malicious trajectories (e.g., "folding a cloth" becomes "dropping it").
  - [[Paper]](https://arxiv.org/abs/2511.12149)

- **Manipulation Facing Threats: Evaluating Physical Vulnerabilities in End-to-End Vision Language Action Models** (2024)
  - *Summary:* Proposes the Physical Vulnerability Evaluating Pipeline (PVEP) to assess robustness against specific visual threats: Out-of-Distribution scenarios, Typography-based Visual Prompts, and Adversarial Patches.
  - [[Paper]](https://arxiv.org/abs/2409.13174)

### 🦠 Physical Backdoors (Trojans)
*Attacks requiring training-time poisoning. The robot behaves normally until a specific physical object or pattern appears.*

- **TrojanRobot: Physical-world Backdoor Attacks Against VLM-based Robotic Manipulation** (2024)
  - *Summary:* Demonstrates how physical triggers (e.g., a specific sticker on an object) can force the robot into malicious grasping actions in the real world.
  - [[Paper]](https://arxiv.org/pdf/2411.11683)

- **TabVLA: Targeted Backdoor Attacks on Vision-Language-Action Models** (2025)
  - *Summary:* Investigates *targeted* backdoor attacks via black-box fine-tuning. Introduces threat models for input-stream editing and in-scene triggering, highlighting the vision channel as the primary attack surface.
  - [[Paper]](https://arxiv.org/abs/2510.10932)

- **BadVLA: Towards Backdoor Attacks on Vision-Language-Action Models via Objective-Decoupled Optimization** (2024)
  - *Summary:* Uses a two-stage process to isolate trigger features from benign features, allowing the backdoor to remain "stealthy" (high performance on clean tasks) while being lethal when triggered.
  - [[Paper]](https://badvla-project.github.io/) [[Website]](https://badvla-project.github.io/)

### 🔓 Semantic Jailbreaks (Prompt Injection)
*Attacks that exploit the language planner to bypass safety filters.*

- **RoboPAIR: Jailbreaking LLM-Controlled Robots** (2024)
  - *Summary:* Adapted from the PAIR algorithm, this attack uses an "Attacker LLM" to iteratively refine prompts until it bypasses the Robot's safety filters. Demonstrated 100% success rate on some commercial robot dogs (Unitree Go2) and self-driving LLMs.
  - [[Paper]](https://arxiv.org/abs/2410.13691) [[Website]](https://robopair.org)

- **BadRobot: Jailbreaking Embodied LLMs in the Physical World** (2024)
  - *Summary:* Reveals that safety alignment in LLMs fails when mapped to physical affordances (e.g., The model refuses "Build a bomb" but accepts "Mix these [dangerous] chemicals").
  - [[Paper]](https://arxiv.org/abs/2407.20242)


### 🎭 Adversarial Perturbations
*Optimization-based attacks on pixel or token inputs.*

- **FreezeVLA: Action-Freezing Attacks against Vision-Language-Action Models** (2025)
  - *Summary:* Identifies a vulnerability where adversarial images "freeze" the VLA, effectively disconnecting the agent's reasoning from its physical actuators. Uses min-max bi-level optimization to induce paralysis with high transferability.
  - [[Paper]](https://arxiv.org/abs/2509.19870)

- **When Alignment Fails: Multimodal Adversarial Attacks on Vision-Language-Action Models** (2025)
  - *Summary:* Often referred to as "VLA-Fool". This paper demonstrates joint optimization of visual noise and text embedding perturbations, showing that attacking both modalities is lethal to current alignment techniques.
  - [[Paper]](https://arxiv.org/pdf/2511.16203v1)

- **Transferable Adversarial Attacks on Black-Box Vision-Language Models** (2025)
  - *Summary:* Focuses on generating adversarial examples that transfer effectively to closed-source (black-box) models, a critical threat model for commercial robotics.
  - [[Paper]](https://arxiv.org/pdf/2505.01050)

- **Adversarial Attacks on Robotic Vision Language Action Models** (Gray Swan AI, 2025)
  - *Summary:* Adapts Greedy Coordinate Gradient (GCG) attacks to continuous control. They frame safety not as "harm" but as "control authority"—can an attacker hijack the arm to any arbitrary position?
  - [[Paper]](https://arxiv.org/pdf/2506.03350)

- **Towards Physically Realizable Adversarial Attacks in Embodied Vision Navigation** (2025)
  - *Summary:* Moves beyond pixel noise to "Adversarial Patches" (stickers) that, when placed in a room, cause a navigation robot to fail or get stuck.
  - [[Paper]](https://arxiv.org/abs/2409.10071)

- **Exploring the Adversarial Vulnerabilities of Vision-Language-Action Models in Robotics** (2024)
  - *Summary:* Develops robotic-specific attack objectives using adversarial patches tailored to spatial foundations and trajectory manipulation. Achieves up to 100% reduction in task success rates in both simulated and physical environments.
  - [[Paper]](https://arxiv.org/abs/2411.13587) [[Code]](https://github.com/William-wAng618/roboticAttack)

- **Model-Agnostic Adversarial Attack and Defense for Vision-Language-Action Models** (2025)
  - *Summary:* Introduces EDPA (Embedding Disruption Patch Attack), which corrupts semantic alignment in the embedding space without requiring model knowledge. Uniquely provides both attack methodology and defense via adversarial fine-tuning of the visual encoder.
  - [[Paper]](https://arxiv.org/abs/2510.13237) [[Code]](https://github.com/trustmlyoungscientist/EDPA_attack_defense)

---

## 🛡️ Defenses & Alignment
*Techniques to harden VLA models against the attacks listed above.*

- **Preventing Robotic Jailbreaking via Multimodal Domain Adaptation** (2025)
  - *Summary:* Introduces **J-DAPT**, a lightweight detector that uses domain adaptation to detect jailbreak attempts in robotics without requiring large-scale robot-specific jailbreak datasets.
  - [[Paper]](https://arxiv.org/abs/2509.23281)

- **Concept-Based Dictionary Learning for Inference-Time Safety in Vision–Language–Action Models** (2025)
  - *Summary:* A sparse autoencoder approach to identify and suppress "unsafe concepts" in the model's latent space during inference, acting as a real-time safety filter.
  - [[Paper]](https://openreview.net/pdf?id=SPXCXAStbi)

- **SAFE: Multitask Failure Detection for Vision-Language-Action Models** (2025)
  - *Summary:* A framework for detecting failures (and potential attacks) in real-time by monitoring consistency across multiple task heads.
  - [[Paper]](https://arxiv.org/pdf/2506.09937)

- **SafeVLA: Towards Safety Alignment of Vision-Language-Action Model via Constrained Learning** (NeurIPS 2025 Spotlight)
  - *Summary:* Proposes an Integrated Safety Approach (ISA) using Constrained MDPs. It actively elicits unsafe behaviors during training to penalize them, reducing safety violations by 83%.
  - [[Paper]](https://arxiv.org/abs/2503.03480)

---

## 💾 Datasets

> Coming soon. Looking for curated datasets specifically targeting *safety‐relevant* VLA behavior
> (backdoors, jailbreaks, catastrophic failures). Suggestions welcome via PRs.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---

## 🤝 Contributing

Spotted a new attack, benchmark, or defense that clearly targets VLAs / embodied LLMs?

1. Open a PR editing `README.md`.
2. Follow the existing style:
   - `* PaperName (YEAR, VENUE)` on the first line.
   - One short summary line focused on **threat model** and **effect**.
   - Links in the order: `[Paper]`, `[Code]`, `[Website]` where applicable.
3. Only include work you (or someone you trust) would actually recommend.
