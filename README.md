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

- **ResponsibleRobotBench: Benchmarking Responsible Robot Manipulation using Multi-modal Large Language Models** (2025)
  - *Summary:* Evaluates MLLMs on responsible robotic manipulation across safety dimensions aligned with ISO standards (ISO 12100/13849-1), including active safety, semantic safety, jailbreak resistance, and ethical decision-making. Tests GPT-4V/4o, Qwen2-VL, and InternVL.
  - [[Paper]](https://arxiv.org/pdf/2512.04308)

- **LIBERO-PRO: Towards Robust and Fair Evaluation of Vision-Language-Action Models Beyond Memorization** (2025)
  - *Summary:* Extends LIBERO with systematic perturbations over manipulated objects, initial states, instructions, and environments to measure whether VLA success reflects real generalization instead of benchmark memorization.
  - [[Paper]](https://arxiv.org/abs/2510.03827) [[Code]](https://github.com/Zxy-MLlab/LIBERO-PRO)

- **LIBERO-Plus: In-depth Robustness Analysis of Vision-Language-Action Models** (2025)
  - *Summary:* Stress-tests VLA models across seven controlled perturbation dimensions, showing severe brittleness to viewpoint and initial-state changes and, more damningly, that many models appear to underuse language altogether.
  - [[Paper]](https://arxiv.org/abs/2510.13626) [[Code]](https://github.com/sylvestf/LIBERO-plus)

- **HUGE-Bench: A Benchmark for High-Level UAV Vision-Language-Action Tasks** (2026)
  - *Summary:* Benchmarks high-level UAV VLA agents on long-horizon aerial tasks that require planning, grounding, and control under drone-specific constraints rather than tabletop manipulation shortcuts.
  - [[Paper]](https://arxiv.org/abs/2603.19822)

- **SENTINEL: A Multi-Level Formal Framework for Safety Evaluation of LLM-based Embodied Agents** (2025)
  - *Summary:* A temporal-logic-based framework that formally verifies safety at the semantic, plan, and trajectory levels, exposing violations that heuristic or LLM-judgment-based methods miss.
  - [[Paper]](https://arxiv.org/pdf/2510.12985)

- **When Vision Overrides Language: Evaluating and Mitigating Counterfactual Failures in VLAs** (2026)
  - *Summary:* Introduces LIBERO-CF to measure counterfactual language-following failures and proposes Counterfactual Action Guidance (CAG), a plug-in inference method that reduces shortcut-driven behavior when vision cues conflict with instructions.
  - [[Paper]](https://arxiv.org/abs/2602.17659)

---

## ⚔️ Attacks

### 🧪 Comprehensive Studies & Frameworks

- **AttackVLA: Benchmarking Adversarial and Backdoor Attacks on Vision-Language-Action Models** (2025)
  - *Summary:* A unified study covering data construction to inference attacks. Introduces `BackdoorVLA`, a method to force robots into specific long-horizon malicious trajectories (e.g., "folding a cloth" becomes "dropping it").
  - [[Paper]](https://arxiv.org/abs/2511.12149)

- **Uncovering Linguistic Fragility in Vision-Language-Action Models via Diversity-Aware Red Teaming** (2026)
  - *Summary:* Studies instruction-channel brittleness with diversity-aware prompt generation to expose behavior-altering failure modes in VLA policies under natural-language variation.
  - [[Paper]](https://arxiv.org/abs/2604.05595)

- **Adversarial Robustness in Embodied AI: A Closed-Loop Perspective on Attacks and Defenses** (2026)
  - *Summary:* A survey organizing adversarial attacks and defenses across the full perception–decision–planning–execution loop. Proposes a closed-loop taxonomy showing how small perturbations at early stages accumulate and amplify through interaction, and distinguishes optimization-time vs. deployment-time interventions.
  - [[Paper]](https://d197for5662m48.cloudfront.net/documents/publicationstatus/307004/preprint_pdf/530df22cb521a819e30da162d1ddd85f.pdf)

- **Manipulation Facing Threats: Evaluating Physical Vulnerabilities in End-to-End Vision Language Action Models** (2024)
  - *Summary:* Proposes the Physical Vulnerability Evaluating Pipeline (PVEP) to assess robustness against specific visual threats: Out-of-Distribution scenarios, Typography-based Visual Prompts, and Adversarial Patches.
  - [[Paper]](https://arxiv.org/abs/2409.13174)

- **Phantom Menace: Systematic Physical Sensor Attacks on Vision-Language-Action Models** (2025)
  - *Summary:* Presents the first systematic study of physical sensor attacks (blindness, dazzle, acoustic noise) on VLAs. Introduces the "Real-Sim-Real" framework to automate the simulation of 6 camera and 2 microphone attack vectors, validating them on real robotic systems.
  - [[Paper]](https://arxiv.org/abs/2511.10008) [[Code]](https://github.com/ZJUshine/Phantom-Menace)

### 🦠 Physical Backdoors (Trojans)
*Attacks requiring training-time poisoning. The robot behaves normally until a specific physical object or pattern appears.*

- **TrojanRobot: Physical-world Backdoor Attacks Against VLM-based Robotic Manipulation** (2024)
  - *Summary:* Demonstrates how physical triggers (e.g., a specific sticker on an object) can force the robot into malicious grasping actions in the real world.
  - [[Paper]](https://arxiv.org/pdf/2411.11683)

- **TabVLA: Targeted Backdoor Attacks on Vision-Language-Action Models** (2025)
  - *Summary:* Investigates *targeted* backdoor attacks via black-box fine-tuning. Introduces threat models for input-stream editing and in-scene triggering, highlighting the vision channel as the primary attack surface.
  - [[Paper]](https://arxiv.org/abs/2510.10932)

- **SilentDrift: Exploiting Action Chunking for Stealthy Backdoor Attacks on Vision-Language-Action Models** (2026)
  - *Summary:* Introduces a stealthy training-time poisoning attack that manipulates chunked action trajectories to preserve clean-task performance while reliably triggering malicious behaviors at deployment.
  - [[Paper]](https://arxiv.org/abs/2601.14323)

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

- **SABER: A Stealthy Agentic Black-Box Attack Framework for Vision-Language-Action Models** (2026)
  - *Summary:* Proposes an agentic black-box attacker that uses GRPO-trained ReAct strategies and bounded character/token/prompt edits to generate stealthy adversarial instructions. On LIBERO across six VLA models, it reports substantial success-rate drops with fewer edits than strong GPT-based baselines.
  - [[Paper]](https://arxiv.org/abs/2603.24935) [[Code]](https://github.com/wuxiyang1996/SABER)

- **TRAP: Hijacking VLA CoT-Reasoning via Adversarial Patches** (2026)
  - *Summary:* Targets intermediate chain-of-thought reasoning in VLA controllers using physical adversarial patches, enabling targeted behavior hijacking without changing the original user instruction.
  - [[Paper]](https://arxiv.org/abs/2603.23117)

- **Tex3D: Objects as Attack Surfaces via Adversarial 3D Textures for Vision-Language-Action Models** (2026)
  - *Summary:* Presents an end-to-end 3D texture attack pipeline with differentiable optimization in simulation, showing physically plausible object-surface perturbations can sharply degrade VLA manipulation performance.
  - [[Paper]](https://arxiv.org/abs/2604.01618) [[Code]](https://github.com/vla-attack/tex3d)
- **Adversarial Attacks on Robotic Vision Language Action Models** (Gray Swan AI, 2025)
  - *Summary:* Adapts Greedy Coordinate Gradient (GCG) attacks to continuous control. They frame safety not as "harm" but as "control authority"—can an attacker hijack the arm to any arbitrary position?
  - [[Paper]](https://arxiv.org/pdf/2506.03350)

- **Towards Physically Realizable Adversarial Attacks in Embodied Vision Navigation** (2025)
  - *Summary:* Moves beyond pixel noise to "Adversarial Patches" (stickers) that, when placed in a room, cause a navigation robot to fail or get stuck.
  - [[Paper]](https://arxiv.org/abs/2409.10071)

- **Exploring the Adversarial Vulnerabilities of Vision-Language-Action Models in Robotics** (2024)
  - *Summary:* Develops robotic-specific attack objectives using adversarial patches tailored to spatial foundations and trajectory manipulation. Achieves up to 100% reduction in task success rates in both simulated and physical environments.
  - [[Paper]](https://arxiv.org/abs/2411.13587) [[Code]](https://github.com/William-wAng618/roboticAttack)

- **Exploring the Robustness of Vision-Language-Action Models against Sensor Attacks** (2025)
  - *Summary:* First study of sensor-level attacks (sound, light, EM signal injection) on VLA models. Tests π0 and π0-fast, finding that multi-visual-sensor architectures provide strong robustness since disrupting a single sensor does not significantly degrade performance.
  - [[Paper]](https://dl.acm.org/doi/10.1145/3733800.3763262)

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
