# DiffusionCompass

> **On-Policy Diffusion Reinforcement Learning Meets Off-Policy Quality Anchoring**  
> ECCV 2026 Official Implementation

<!--
Project page, arXiv, checkpoints, and training code will be updated progressively.
Replace the placeholder links below after the release is ready.
-->

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/Paper-ECCV%202026-blue"></a>
  <a href="#"><img src="https://img.shields.io/badge/arXiv-coming%20soon-b31b1b"></a>
  <a href="#"><img src="https://img.shields.io/badge/Code-coming%20soon-lightgrey"></a>
  <a href="#"><img src="https://img.shields.io/badge/Models-coming%20soon-lightgrey"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-TBD-yellow"></a>
</p>

<p align="center">
  Zunxu Liu<sup>1</sup>, Zhaofan Qiu<sup>2</sup>, Yazhen Xie<sup>3</sup>, Yingwei Pan<sup>2</sup>, Ting Yao<sup>2</sup>, Tao Mei<sup>2</sup>
</p>

<p align="center">
  <sup>1</sup>University of Science and Technology of China &nbsp;&nbsp;
  <sup>2</sup>HiDream.ai Inc. &nbsp;&nbsp;
  <sup>3</sup>Fudan University
</p>

## News

Code, checkpoints, and scripts are being organized.
DiffusionCompass is accepted to ECCV 2026.

## Overview

DiffusionCompass is a reinforcement learning framework for diffusion model post-training. Existing on-policy diffusion RL methods optimize the model using samples from the current policy, which provides a direct reward signal but can become self-limiting: the model may overfit local reward maxima, lose diversity, or collapse when its own samples no longer provide reliable optimization directions.

DiffusionCompass augments on-policy exploration with **off-policy quality anchoring**. The model still explores reward maximization with online samples, while high-quality off-policy examples provide a stable external reference for what good generations should look like. This combination acts as a "compass" for policy updates, improving reward performance, convergence speed, and robustness against reward hacking.

## Method

DiffusionCompass combines three key ideas:

- **Distribution-aware off-policy anchoring:** use off-policy samples as quality anchors while filtering them according to their relevance to the current policy.
- **Perceptual anchored reward:** encourage on-policy samples to stay close to reliable high-quality references, reducing reward hacking.
- **Reward renormalization:** normalize rewards with off-policy samples to provide a stable quality baseline for on-policy learning.

<p align="center">
  <img src="assets/fig/framework_crop.pdf" width="90%">
</p>

<p align="center">
  <b>Figure:</b> Overall framework of DiffusionCompass.
</p>

## Motivation

The figures below are reused from the paper draft as placeholders. They focus on the core idea rather than benchmark comparisons, and can be replaced with PNG assets before the public release for better GitHub rendering.

<p align="center">
  <img src=".assets/fig/intro_a.pdf" width="42%">
  <img src=".assets/fig/intro_b.pdf" width="42%">
</p>

<p align="center">
  <b>Figure:</b> on-policy-only optimization versus on-policy exploration with off-policy quality anchoring.
</p>

## Highlights

- Strong post-training framework for text-to-image and text-to-video diffusion models.
- Combines on-policy RL with off-policy quality references.
- Mitigates reward overfitting, reward hacking, and mode collapse.
- Compatible with different on-policy diffusion RL objectives.

## TODO

- [ ] Release training code.
- [ ] Release inference scripts.
- [ ] Release evaluation scripts for GenEval, OCR, PickScore, and VBench.
- [ ] Release configuration files.
- [ ] Release checkpoints and LoRA weights.
- [ ] Add dataset preparation instructions.
- [ ] Add detailed reproduction commands.

## Installation

The repository is under active cleanup. The final environment file will be released with the code.

```bash
git clone https://github.com/your-org/DiffusionCompass.git
cd DiffusionCompass

# coming soon
conda create -n diffusioncompass python=3.10
conda activate diffusioncompass
pip install -r requirements.txt
```

## Quick Start

Training and inference scripts will be added soon.

```bash
# Prepare off-policy anchors
python tools/build_off_policy_bank.py --config configs/t2i/compass_sd35_ocr.yaml

# Text-to-image post-training
accelerate launch scripts/train_compass_t2i.py --config configs/t2i/compass_sd35_ocr.yaml

# Inference
python scripts/sample_t2i.py --config configs/t2i/inference.yaml --checkpoint /path/to/checkpoint

# Text-to-video post-training
accelerate launch scripts/train_compass_t2v.py --config configs/t2v/compass_wan_vbench.yaml
```

## Evaluation

Evaluation scripts will cover the main benchmarks used in the paper:

- GenEval for compositional image generation.
- OCR benchmark for visual text rendering.
- PickScore for human preference alignment.
- VBench for comprehensive video generation.
- ImageReward and VideoOCR for additional generalization studies.

```bash
# coming soon
python evaluation/eval_geneval.py --config configs/eval/geneval.yaml
python evaluation/eval_ocr.py --config configs/eval/ocr.yaml
python evaluation/eval_vbench.py --config configs/eval/vbench.yaml
```

## Citation

If you find this work useful, please consider citing:

```bibtex
@inproceedings{liu2026diffusioncompass,
  title     = {On-Policy Diffusion Reinforcement Learning Meets Off-Policy Quality Anchoring},
  author    = {Liu, Zunxu and Qiu, Zhaofan and Xie, Yazhen and Pan, Yingwei and Yao, Ting and Mei, Tao},
  booktitle = {European Conference on Computer Vision},
  year      = {2026}
}
```

## Acknowledgements

This implementation builds on Flow-GRPO and DiffusionNFT. We thank the authors for their inspiring work and open-source contributions.

## License

The license will be specified before the official code release.





