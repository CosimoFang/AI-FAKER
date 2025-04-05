<p align="center">
  <img src="images/ai-faker.png" alt="AI-Faker" width="300">
</p>
<p align="center">
  <a href="https://github.com/CosimoFang/AI-FAKER"><b>AI-FAKER</b></a>
</p>
<p align="center">
  <b>A Comprehensive Benchmark for Detecting, Attributing, and Explaining AI-Generated Images and Text</b>
</p>
<p align="center">
  <a href="https://github.com/CosimoFang/AI-Faker">
    <img src="https://img.shields.io/github/actions/workflow/status/your-username/AI-Faker/lint.yml?logo=githubactions&logoColor=white&label=Code%20Style" alt="Code Style"/>
  </a>
  <a href="https://github.com/your-username/AI-Faker/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License"/>
  </a>
  <a href="https://arxiv.org/abs/XXXXXXXX">
    <img src="https://img.shields.io/badge/arXiv-XXXXXXXX-b31b1b.svg" alt="arxiv"/>
  </a>
</p>

**AI-Faker** is a large-scale multimodal dataset introduced in the paper  
[**Could AI *Trace* and *Explain* the Origins of AI-Generated Images and Text?**](https://arxiv.org/abs/XXXXXXXX)  
It comprises over **280,000** samples spanning different generative AI models:
- **AI-Generated Images** vs. **AI-Modified Images**  
- **AI-Text Completion** vs. **AI-Generated Peer Reviews**  
- **General Use Cases** vs. **Malicious Use Cases**

AI-Faker is intended to be the go-to dataset for **model attribution**, **explanation**, and **robust forgery detection** across multiple modalities.

---

## Table of Contents
- [Key Features](#key-features)
- [Installation](#installation)
- [Dataset Overview](#dataset-overview)
- [Comparison](#comparison)
- [Loading the Dataset](#1-loading-the-dataset)
- [Citation](#citation)
- [License](#license)

---

## Key Features

- **Multimodal Coverage**: Spans both **visual** (fully and partially AI-generated images) and **textual** (short text completions and long-form peer reviews) content.
- **General vs. Malicious Use Cases**: Investigates standard generative tasks (e.g., text-to-image) alongside high-stakes misuse (e.g., face-swapping, AI-written academic reviews).
- **Model Diversity**: Includes outputs from popular **LMMs** (Midjourney, DALL-E, Stable Diffusion, etc.) and **LLMs** (GPT-4, Claude, LLaMA, etc.).
- **Explainability Benchmark**: Offers a unique testbed for **explanation generation**—whether an AI model (e.g., GPT-4) can **explain** *why* an image or text is attributed to a specific generator.

---

## Installation

You can clone this repository and install dependencies from `requirements.txt`:
```bash
git clone https://github.com/your-username/AI-Faker.git
cd AI-Faker
pip install -r requirements.txt
```


## Dataset Overview
Subset	Description	# Instances	Category
AI-Generated Images	Fully diffused from text prompts (DALL-E, Midjourney).	50,000+	General
AI-Modified Images	Partially modified (face-swapped)	28,551	Malicious
AI-Text Completion	Short text completions (GPT-4, Cohere, LLaMA...)	50,000+	General
AI-Paper Review	Full-length peer reviews generated by LLMs	70,000	Malicious
<img src="images/dataset.png" alt="AI-Faker" width="900">

## Comparison:
<img src="images/data.png" alt="AI-Faker" width="900">


## Download the dataset

Run a baseline classifier for forgery detection and model attribution

Evaluate the performance and see if your approach is robust across all AI-Faker subsets


## Citation
If you find AI-Faker or its accompanying code valuable for your research, please cite our paper:
```bibtex
@article{ExampleAIFaker,
  title={Could AI Trace and Explain the Origins of AI-Generated Images and Text?},
  author={Hippocampus, Antiquus S. and Cerebro, Natalia and Amygdale, Amelie P. and Ren, Ji Q. and LeNet, Yevgeny, and others},
  journal={COLM Conference},
  year={2025},
  note={Data and code to be released at https://github.com/your-username/AI-Faker}
}
```
