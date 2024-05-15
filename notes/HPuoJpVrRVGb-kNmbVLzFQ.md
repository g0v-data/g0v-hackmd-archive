# AIGC 3D相關技術
## Overview
1. 3D native generative methods：完全使用3D dataset訓練
2. 2D prior-based 3D generation：使用2D diffusion prior幫助生成未知的View
3. hybrid 3D generative methods：比如zero 1to3，將2D diffusion model finetune在3D dataset上

### template
* Category:
* Introduction:
* Advantages:
* Disadvantages:
* Link:(paper, github, introduction articles or videos...)


## Dreamfusion
* Category: Text to 3D
* Introduction: SDS的開山鼻祖
## Dreamgaussian

## LucidDreamer

## DreamCraft3D

## RichDreamer（CVPR2024）
* Category: Text to 3D
* Introduction: 
* Link: https://zhuanlan.zhihu.com/p/675972851


## GaussianDiffusion
* Category: Text to 3D
* Introduction:使用structured noise讓SDS能更好地引導3D reconstruction

## Zero 1-to-3
* Category: Finetune
* Introduction: 使用大量多視角data做finetune，並在輸入引入camera pose，使模型能生成有一致性的novel views
* Advantages: 有感知方向的能力，用在3D reconstruction任務中時可以保持目標的consistency
* Disadvantages: 由於經過大量data finetune，可能失去原本的能力，比如多樣性及高質量的結果
* Link:

## ViVid-1-to-3
* Category: single image to 3D
* Introduction: 用video diffusion版本的Zero 1-to-3

## Repaint123
* Category: single image to 3D
* Link: https://zhuanlan.zhihu.com/p/676660836

## GPT-4V(ision) is a Human-Aligned Evaluator for Text-to-3D Generation
* Introduction: 使用GPT-4V幫助評量Tto3D model

## HarmonyView: Harmonizing Consistency and Diversity in One-Image-to-3D

DreamComposer: Controllable 3D Object Generation via Multi-View Conditions

Learn to Optimize Denoising Scores for 3D Generation: A Unified and Improved Diffusion Prior on NeRF and 3D Gaussian Splatting

Sherpa3D: Boosting High-Fidelity Text-to-3D Generation via Coarse 3D Prior

RichDreamer

GaussianDreamer: Fast Generation from Text to 3D Gaussians by Bridging 2D and 3D Diffusion Models

GaussianDiffusion: 3D Gaussian Splatting for Denoising Diffusion Probabilistic
Models with Structured Noise