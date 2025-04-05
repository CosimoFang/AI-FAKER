<p align="center">
  <img src="assets/aifaker_logo.png" alt="AI-Faker" width="300">
</p>
<p align="center">
  <a href="https://github.com/your-username/AI-Faker"><b>https://github.com/your-username/AI-Faker</b></a>
</p>
<p align="center">
  <b>A Comprehensive Benchmark for Detecting, Attributing, and Explaining AI-Generated Images and Text</b>
</p>
<p align="center">
  <a href="https://github.com/your-username/AI-Faker/actions/workflows/lint.yml">
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
- [Quick Start](#quick-start)
- [Usage](#usage)
  - [1. Loading the Dataset](#1-loading-the-dataset)
  - [2. Running a Baseline Detector](#2-running-a-baseline-detector)
  - [3. Evaluating Performance](#3-evaluating-performance)
- [Leaderboards](#leaderboards)
- [Contributing](#contributing)
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
Note: We will release the official code and additional scripts upon acceptance of our paper.

Dataset Overview
Subset	Description	# Instances	Category
Original Images	Natural images (e.g., from ImageNet).	10,000	Real
AI-Generated Images	Fully diffused from text prompts (DALL-E, Midjourney).	50,000+	General
AI-Modified Images	Partially modified (face-swapped)	28,551	Malicious
Original Text	Human-authored corpora (news, reviews, etc.)	10,000	Real
AI-Text Completion	Short text completions (GPT-4, Cohere, LLaMA...)	50,000+	General
AI-Paper Review	Full-length peer reviews generated by LLMs	70,000	Malicious
Highlights:

AI-Generated Images from 5 major diffusion models.

AI-Modified Images from 4 face-swapping frameworks.

AI-Text Completion from 5 mainstream LLMs (both open- and closed-source).

AI-Paper Review mimics peer-review misuse with 6 LLMs for professional reviews.

Quick Start
Below is an example usage flow. You will see how to:

Download the dataset

Run a baseline classifier for forgery detection and model attribution

Evaluate the performance and see if your approach is robust across all AI-Faker subsets

python
from aifaker import load_aifaker_data, run_detection, run_evaluation

# 1. Download & Load a subset of the dataset
# This will automatically fetch the data from a public URL, or from a local cache if available
train_df, test_df = load_aifaker_data(subset="AI-paper-review")

# 2. Define your own detection function
def my_detector(batch_texts_or_images):
    """
    Return predictions:
    For text: e.g., your custom classification logic
    For images: e.g., a CNN-based classifier
    """
    # toy example: label everything as "human" with confidence 0.1
    return [0.1] * len(batch_texts_or_images)

# 3. Run detection on the test set
predictions = run_detection(my_detector, test_df)

# 4. Evaluate your predictions
report = run_evaluation(predictions, test_df)
print(report)
Usage
1. Loading the Dataset
Option A: Use our built-in Python function load_aifaker_data(...) (requires an internet connection for initial download).

Option B: Manually download each .csv or .json from our GitHub Releases or a self-hosted HuggingFace dataset, then load it with standard data libraries (e.g., pandas, json).

2. Running a Baseline Detector
We provide reference implementations of baseline detectors in baselines/. For example:

Image: Classification networks like ResNet, ViT, and PNASNet.

Text: BERT, GPT-2, logistic regression on embeddings, etc.

Sample usage of a baseline text detector:

bash
python baselines/text_classifier.py \
  --train_file data/AI_textcompletion_train.csv \
  --test_file data/AI_textcompletion_test.csv \
  --model_name bert-base-uncased
3. Evaluating Performance
After obtaining predictions (e.g., a JSON file containing [0..1] confidence scores for each test instance), you can evaluate:

bash
python evaluation/eval.py \
  --pred_file results/my_predictions.json \
  --gold_file data/AI_textcompletion_test.csv \
  --output_file results/my_evaluation.json
This script calculates metrics like F1 score, Precision/Recall, and optional advanced metrics like Calibration Error.

Leaderboards
We maintain leaderboards for each of the four main tasks:

AI-Generated Images

AI-Modified Images (Face-Swapping)

AI-Text Completion

AI-Paper Review

To appear on the leaderboards, you can submit your predictions file via a Pull Request to our Leaderboard Repo. The format and evaluation scripts mirror the example usage shown above.

Contributing
We welcome all contributions! To get involved:

Fork this repository and create your feature branch.

Develop your new detector, explainer, or analysis module.

Write tests or notebooks showcasing your addition.

Open a Pull Request to the main branch.

You can also open issues if you run into any bugs or have feature requests!

Citation
If you find AI-Faker or its accompanying code valuable for your research, please cite our paper:

bibtex
@article{ExampleAIFaker,
  title={Could AI Trace and Explain the Origins of AI-Generated Images and Text?},
  author={Hippocampus, Antiquus S. and Cerebro, Natalia and Amygdale, Amelie P. and Ren, Ji Q. and LeNet, Yevgeny, and others},
  journal={COLM Conference},
  year={2025},
  note={Data and code to be released at https://github.com/your-username/AI-Faker}
}
License
This project is licensed under the MIT License - see the LICENSE file for details.

Disclaimer
The dataset contains AI-generated content, some of which may be realistic or manipulative. Use caution and follow ethical guidelines when handling or distributing this dataset. Always verify intellectual property rights and privacy regulations, especially regarding images with identifiable faces.

<p align="center"> <b>Happy detecting and attributing!</b> </p> ```
