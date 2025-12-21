
- [Concept](#concept)
- [Evolution](#evolution)
- [Architecture](#architecture)
- [Learning Method](#learning-method)
- [Lifecycle](#lifecycle)
- [Fine-Tuning Techniques](#fine-tuning-techniques)
  - [Instruction-Based Fine-Tuning](#instruction-based-fine-tuning)
  - [Domain Adaptation Fine-Tuning](#domain-adaptation-fine-tuning)
- [Performance Metrics](#performance-metrics)
- [Agent Mode Comparison](#agent-mode-comparison)


Generative AI is a subset of Deep Learning because it can adapt models built using
Deep Learning, but without retraining or fine tuning.

Generative AI is capable of generating new data based on the patterns and structures
learned from training data.

Generative AI is a type of AI that aims to create new content such as images, text, music,
or conversations.

## Concept
- Prompt: the text or input that pass into the model, which can include instructions, context, and constraints to accomplish a given task
- Inference: the process of using a trained model with new data to make predictions and conclusions
- Vector: a list of numbers and that location in a space
- Model Inversion: when an attacker can infer training data by iteratively refining their input data until a high-confidence output is produced
- Embedding: vector representation of content that captures semantic relationships, which provides content with similar meanings to have close vector representations
- AI agent: software systems that use artificial intelligence to reason, plan, and complete tasks on behalf of humans or other systems


## Evolution
Human Oversight Involvement
1. Generative AI Assistant
    - characteristic
        - follow a set of rules
        - repetitive task automation
    - application
        - powerful LLM capability
        - prompt engineering
        - Retrieval Augmented Generation
2. Generative AI Agent
    - characteristic
        - achieve single goals
        - broader task automation
        - full workflow automation
    - application
        - powerful LLM capability
        - memory
        - planning skills + tool use
        - tool use
3. Agentic AI System
    - characteristic
        - full automation
        - multi AI agents
        - simulate human logic and reasoning
    - application
        - easily assemble agents and knowledge bases
        - plan and execute complex tasks across agents
        - unify conversations across agents with built-in intent classification
        - observability across multi-agent flows
        - guardrails, security and privacy

| Agent Intelligent Level | Autonomy Level | Description |
| --- | --- | --- |
| 1 | rule-based automation | all systems based on rules and scripts with predetermined actions |
| 2 | ML-assisted automation | ML-based agents assist with specific deterministic tasks |
| 3 | partial automation | autonomous planning for well-defined use cases |
| 4 | high automation | autonomous execution with sensor access and learning from experience |
| 5 | full automation | complete independence with original thinking, personality, and emotions |

## Architecture
- GANs: Generative Adversarial Networks
- VAEs: Variational AutoEncoders
- Transformers

GenAI Model:
- GANs: Generative Adversarial Networks
- VAEs: Variational AutoEncoders
- Transformers
- RNNs: Recurrent Neural Networks
- Transformer
- Reinforcement Learning for Generative Tasks
- Diffusion
- FLow-based
- BERT: Bidirectional Encoder Representation from Transformers
- GPT: Generative Pre-trained Transformer
- Amazon Titan foundation models
- Jurassic-2
- Claude-2
- Cohere
- Stable Diffusion
- Bloom


## Learning Method
- Zero-Shot Learning/Prompting:
    - help models generalize to new tasks or contexts without directly training examples
    - is useful when working with limited or no labeled data because the model can infer from related concepts
- Single-Shot Learning/Prompting:
    - involve learning from a single example of a class or concept
    - is suitable for situations where data is extremely limited, but meaningful learning can occur from one instance
- Few-shot Learning/Prompting:
    - involve training a model with a small number of examples, typically 2 – 10
    - provides some generalization but requires fewer resources than traditional deep learning methods


## Lifecycle
Define user case
-> Select a foundation model
-> Improve performance
-> Evaluate results
-> Deploy the application

Well-defined business case:
- use case name
- brief description
- actors
- preconditions
- basic flow (main success scenario)
- alternative flows (extensions)
- postconditions
- business rules
- nonfunctional requirements
- assumption
- notes or additional information


## Fine-Tuning Techniques
Fine-tuning is the process of providing labeled data to train a model to improve model performance:
- can increase performance in domain-specific tasks
- can support the generation of more contextual responses

Continued pre-training is the process of providing unlabeled data to pre-train a
model, where Fine-tuning would take more operational overhead than pre-training.

Type:
- PEFT: Parameter-Efficient Fine-Tuning
- LoRA: Low-Rank Adaptation
- ReFT: Representation Fine-Tuning
- RLHF: Reinforcement Learning from Human Feedback
- Multitask Fine-Tuning
- Domain adaptation Fine-Tuning: can expand an LLM's knowledge of a given domain, such as learning about industry jargon or technical terms
- Instruction-based Fine-Tuning: use labeled data to improve large language model (LLM) performance on a specific task, which helps to teach a model how to correspond with users in a multi-turn chatbot environment

### Instruction-Based Fine-Tuning
- a technique to improve the performance and generated results of a model by providing labeled examples on a specific task
- uses labeled data to improve large language model (LLM) performance on a specific task
- can be used to teach a model how to correspond with users in a multi-turn chatbot environment

### Domain Adaptation Fine-Tuning
- a method used to customize a pre-trained FM by fine-tuning the model on a specific task or domain-specific information
- improve the performance of an FM by fine-tuning the model on industry-specific terminology


## Performance Metrics
- ROUGE: Recall Oriented Understudy for Gisting Evaluation
  - assess the quality of machine-generated text by evaluating the difference between system-generated and reference texts
  - provides insight into how well the generated text captures the content and structure of the reference text
- BLEU: BiLingual Evaluation Understudy
- GLUE: General Language Understanding Evaluation
- HELM: Holistic Evaluation of Language Models
- MMLU: Massive Multitask Language Understanding
- BIG-bench: Beyond the Imitation Game Benchmark

- BERTScore: a metric used to evaluate the quality of text that is generated by a text-to-text language model, which measures the semantic similarity between the generated text and the reference text
- Perplexity: a metric used to evaluate language models, which measures the probability of a model to generate a given sequence of words.


## Agent Mode Comparison
| Feature | Agents as Tools | Agent Graph | Workflow |
| --- | --- | --- | --- |
| Architecture | coding scheduler with professional "tool intelligence" | persistent graph of interconnected agents | structured coordination of multiple agent tasks in a defined sequence or pattern |
| Topology | flexible (star) | flexible (star, mesh, hierarchical) | flexible |
| Communication | passing message as tool input | direct messaging between nodes | passing context between tasks |
| Continuity | short-term, task-focused | long-term execution, stateful | long-term execution, stateful |
| Use Cases | complex or diverse tasks with specialized agent roles | workflow with specialized agent roles | scenarios that require structured execution and clear dependencies |
| Complexity | lower (easier to set up and use) | higher (more configuration options) | higher (more configuration options) |
