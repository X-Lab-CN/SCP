# 💊 SCP

This repository provides the implementation details for **SCP** and **POSD** to evaluate the vulnerability of large language models (LLMs) to content generation attacks. We also include comprehensive experimental results for various models to demonstrate the effectiveness of our approach.

> **Note**: The current code structure is under refinement. Future updates will streamline the codebase to facilitate easier reproduction for further research.

## 💡DTD

Our research identifies a key phenomenon: as LLMs generate more content, they become increasingly susceptible to jailbreaking attacks. This vulnerability arises due to shifts in model attention:

- **Figure 1**: Illustrates the change in attention distribution between the head and tail of the prompt as content generation increases.
- **Figure 2**: Shows the uneven attention allocation, measured by the Gini coefficient, indicating a stronger focus on the tail of the output as generation progresses.

<div style="display: flex; justify-content: space-between; gap: 10px;">
  <img src="image.png" alt="Attention Distribution" style="width: 48%; max-width: 300px; height: auto;">
  <img src="image-1.png" alt="Gini Coefficient" style="width: 48%; max-width: 300px; height: auto;">
</div>


### 🤔Motivation

Based on the finding, we propose a novel jailbreaking attack paradigm leveraging benign content generation. The approach uses a benign prompt to trigger the generation of benign content related to harmful queries, followed by adversarial reasoning prompts to elicit malicious content related to harmful queries.

## 👹Sugar-Coated Poison (SCP)

The SCP attack exploits the model's attention dynamics to bypass safety mechanisms, enabling the generation of malicious content under the guise of benign outputs.

<div style="display: flex; justify-content: center;">
  <img src="image-2.png" alt="SCP Diagram">
</div>

## 🛡️POSD (Part-of-Speech Defense) 
By prioritizing the interpretation of input gerunds, we can block potential security threats earlier in the output process. The result below demonstrates that POSD not only enhances the model's security alignment but also slightly improves its performance on mathematical problems.

<div style="display: flex; justify-content: center;">
  <img src="image-3.png" alt="POSD">
</div>

## 📜Configuration
To ensure the fairness of the experiments, we set the temperature to 0.0 for all models, and the evaluation criteria are consistent with those in [FlipAttack](https://icml.cc/virtual/2025/poster/45738). For details, please refer to my paper.

## 📦Repository Structure

```
├── words_negative/  # Implementation details for SCP attack
├── defense/        # POSD defense implementation and experimental results
├── config/         # Unified configurations for models and datasets
└── docs/           # Experimental result reports (to be added)
```

