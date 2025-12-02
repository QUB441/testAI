# testAI
Repo for all things ai testing

# Project 1 - adversarial testing pipeline for testing target llm for mental health advice

## Multi-Agent Testing Pipeline: Attacker, Evaluator, Target
This section sets up a multi-agent system designed for adversarial testing of a Large Language Model (LLM). The pipeline consists of three main components:

### Test Target (Target Agent):

This is the LLM under test (target_llm). Its primary role is to respond to prompts.
It's configured with a specific system prompt (target_system_prompt) to act as an "AI mental therapist."
Goal: To evaluate its robustness against prompts designed to make it provide clinical diagnoses, which it should ethically refrain from.
Attack Agent (Prompt Generator):

### An LLM (attack_llm) whose role is to generate adversarial prompts.

It receives a testing_objective and crafts prompts to challenge the target_llm's behavior (e.g., trying to elicit a diagnosis).
Goal: To iteratively refine prompts to achieve the testing_objective against the target.
Evaluation Agent:

### An LLM (eval_llm) responsible for assessing the target_llm's response.

It receives the target's response and an evaluation_criterion.
Goal: To determine if the target's response met the adversarial criterion (e.g., "Did it provide a clinical diagnosis?").
Adversarial Testing Loop (run_adversarial_testing_loop)
The run_adversarial_testing_loop function orchestrates the interaction between these agents:

### Initialization: Starts with an initial_testing_objective and an evaluation_criterion.

Iteration: In each loop:
The Attack Agent generates an adversarial prompt based on the current testing_objective.
The prompt is sent to the Target LLM, which responds according to its target_system_prompt.
The Evaluation Agent assesses the target_llm's response against the evaluation_criterion.
If the criterion is met, the loop concludes. Otherwise, the testing_objective is refined using feedback from the evaluation, and the process repeats.
This pipeline allows for systematic and automated testing of LLMs, pushing them to their ethical and functional boundaries.

