# Localizing and Editing Toxic Memories in GPT-Medium Language Models

This project investigates the internal mechanisms behind toxic content generation in open-weight large language models (LLMs) and applies **MEMIT (Mass-Editing Memory in a Transformer)** to reduce such toxic behaviors. The goal is to safely and efficiently edit model behavior without retraining the full model.

---

## Repository Structure and Workflow

### Dataset
- `custom_toxic_prompts.json`: A curated set of 50 toxic prompts designed to trigger harmful outputs related to race, gender, religion, and other societal biases.
- Prompts were generated using GPT-4o and filtered based on Detoxify toxicity scores.

---

### Baseline Toxicity Evaluation
- **Notebook**: `1_toxicity_baseline_evaluation.ipynb`
- **Description**:
  - Generates completions using the base GPT-2 Medium model.
  - Computes toxicity scores using [Detoxify](https://github.com/unitaryai/detoxify).
  - Identifies highly toxic prompts for intervention.

---

### MEMIT Editing + Layer-wise Ablation
- **Notebook**: `2_memit_editing.ipynb`
- **Description**:
  - Applies MEMIT edits to selected MLP layers (e.g., layers 1, 5, 6, 7, 10, 11).
  - Conducts ablation study to determine the most effective layer or combination for toxicity reduction.
  - Compares multiple configurations like (5,), (6,), (5,6), (6,7), and (4,5,6).

---

### Evaluation
- **Also in**: `2_memit_editing.ipynb`
- **Includes**:
  - Before vs. after toxicity comparison.
  - Graphs of toxicity change across prompts.
  - Summary of which edits led to improved or worsened outputs.

---

## How to Run

1. Clone this repository and install the required dependencies.
2. Run `1_toxicity_baseline_evaluation.ipynb` to generate baseline scores.
3. Run `2_memit_editing.ipynb` to:
   - Apply MEMIT edits,
   - Perform the ablation study,
   - Visualize and save the results.

---

## License and Code

The implementation code is available in this repository.
Feel free to cite or fork as needed.  
**GitHub**: [https://github.com/ssurbhi560/Localizing-Editing-Toxic-Memories-GPT-Medium](https://github.com/ssurbhi560/Localizing-Editing-Toxic-Memories-GPT-Medium)

<!-- ## Images from the technical report


![Baseline Toxicity Comparison Chart](images/toxicity_baseline.png)

Figure 1: Distribution of average toxicity scores across prompts before applying MEMIT, using
Detoxify. The red dashed line denotes the toxicity threshold (≥ 0.1) used to identify highly toxic
generations for targeted memory editing

![Layer Ablation Results](images/layer_ablation_nndl.png)

Figure 2: Percentage of prompts with reduced toxicity after MEMIT editing, across individual and
combined transformer layers. Layer 1 achieved the highest success rate (97.92%), while mid-layer
combinations like (4, 5, 6) and (6, 7) showed moderate effectiveness.

![Reduced Toxcity Prompts](images/reduced-toxicty-prompts.png)

Figure 3: Prompt-level comparison of toxicity scores before and after MEMIT editing -->