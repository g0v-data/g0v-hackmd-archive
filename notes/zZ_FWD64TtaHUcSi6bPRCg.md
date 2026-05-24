 1. Minority/tail generation đã có
      - Don’t Play Favorites: Minority Guidance for Diffusion Models, ICLR 2024: diffusion thiên về majority modes, họ guide sampler về low-density/minority
        samples. Đây là đối thủ trực tiếp nhất về motivation long-tail.
        Nguồn: ICLR 2024 (https://proceedings.iclr.cc/paper_files/paper/2024/hash/5dc387343572bb95f264e05b66e83951-Abstract-Conference.html)
      - Self-Guided Generation of Minority Samples Using Diffusion Models, ECCV 2024: self-contained guidance dùng pretrained diffusion, không classifier
        ngoài.
        Nguồn: ECCV PDF (https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/08641.pdf)
      - Generative Data Mining with Longtail-Guided Diffusion, ICML 2025 poster: dùng epistemic uncertainty/longtail signals để guide latent diffusion tạo
        data cho training. Đây rất gần motivation “generate rare valid samples for retraining”.
        Nguồn: arXiv (https://arxiv.org/abs/2502.01980)
  2. Uncertainty của score/diffusion đã có
      - BayesDiff, ICLR 2024: Bayesian inference/last-layer Laplace để estimate pixel-wise uncertainty trong diffusion generation. Không phải long-tail SDE
        design, nhưng reviewer sẽ cite nó nếu bạn nói “Bayesian uncertainty in diffusion” quá rộng.
        Nguồn: OpenReview PDF (https://openreview.net/pdf/a89f50009d9d43c9ab257ef46f36abf04f1c05a4f1c05a4.pdf), arXiv (https://arxiv.org/abs/2310.11142)
      - Score-based generative models are provably robust: an uncertainty quantification perspective, NeurIPS 2024: propagation của score error qua Fokker-
        Planck/Wasserstein bound. Đây là prior art lý thuyết mạnh về “score approximation uncertainty”.
        Nguồn: NeurIPS (https://proceedings.neurips.cc/paper_files/paper/2024/hash/7371b5f5fab9fd401c4ebd352f29dc48-Abstract-Conference.html)
      - Modeling Score Approximation Errors in Diffusion Models via Forward SPDEs, arXiv 2026: xem score error như stochastic source trong density evolution/
        SPDE. Preprint, nhưng rất gần về mặt “random score perturbation”.
        Nguồn: arXiv (https://arxiv.org/abs/2602.08579)
  3. Flow matching extension đã bắt đầu có
      - Stochastic Interpolants, JMLR 2025: framework unify flows và diffusions, có deterministic/stochastic generative dynamics với adjustable noise. Đây là
        nền toán để extend diffusion idea sang flow matching.
        Nguồn: JMLR (https://jmlr.org/beta/papers/v26/23-1605.html)
      - Flow Matching with Uncertainty Quantification and Guidance / UA-Flow, arXiv 2026: velocity field + heteroscedastic uncertainty + uncertainty-guided
        sampling. Đây rất gần nếu bạn extend sang flow matching bằng uncertainty.
        Nguồn: arXiv (https://arxiv.org/abs/2602.10326)


2. Claim tốt hơn:
      - First to formulate heteroscedastic score epistemic uncertainty as a tail exploration control for long-tailed generative augmentation.
      - Derive three regimes: frozen Bayesian drift, discrete stochastic score sampler, and continuous multiplicative-noise reverse SDE.
      - Show naïve stochastic score noise vanishes in continuous time unless properly scaled.
      - Propose corrected uncertainty-controlled reverse SDE / probability-flow counterpart.
      - Extend to flow matching by learning vθ(x,t) plus Σv(x,t) and adding uncertainty-guided velocity/noise.
      - Evaluate on tail coverage, not only FID.
