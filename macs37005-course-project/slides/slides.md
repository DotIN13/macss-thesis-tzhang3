---
title: "Probing Political Ideology in LLMs"
subtitle: "Latent Representations, Behavioral Impact, and Social Implications"
author: Tianyi Zhang
theme: apple-basic
layout: intro
fonts:
  # basically the text
  sans: Palatino Linotype
  # for code blocks, inline code, etc.
  mono: Fira Code
---

# Probing Political Ideology <br> in LLMs <br> <span style="font-size: 2.5rem; color: #888">(And across Modalities)</span>

Peter Zhang · March 2026

<style>
h1 {
  margin-bottom: 5rem !important;
}
</style>

---

# 1.1 Research Question

How do Language Models map our real-world political landscapes into their latent representations?
  
- **In Text**: How does the model encode political *intentions*, *opinions* and *rhetoric*?
- **In Vision**: How does the model encode political figures (*people*) and associated *symbols*?

<style>
h1 {
  margin-bottom: 3rem !important;
}

p, ul {
  font-size: 1.8rem;
}

p {
  line-height: 1.5;
}

li {
  line-height: 1.5;
}
</style>

---

# 1.2 Linear Dimension of Political Ideology  

<figure>
  <img src="./figures/political_probe_overview.png" alt="Political Probe Overview">
  <figcaption style="font-size: 0.8rem; color: #888; text-align: center; margin-top: 0.5rem;">
    Adapted from: Li, K., Patel, O., Viégas, F., Pfister, H., & Wattenberg, M. (2023). Inference-time intervention: Eliciting truthful answers from a language model. <i>Advances in Neural Information Processing Systems</i>, 36, 41451-41530.
  </figcaption>
</figure>

<style>
h1 {
  margin-bottom: 3rem !important;
}
</style>

---

# 2.1 Ideology Generalizes to Behavioral Dimensions

<div class="grid grid-cols-2 gap-4">

  <div>
    <h3 style="opacity: 0.8">Is the statement liberal/conservative?</h3>
    <img src="./figures/sankey_plot.png" style="width: 100%; border-radius: 4px;" alt="Sankey Plot" />
  </div>

  <div>
    <h3 style="opacity: 0.8">Rewrite statement to be neutral.</h3>
    <img src="./images/bias_neutralization.png" style="width: 100%; border-radius: 4px;" alt="Bias Neutralization Table" />
  </div>

</div>

<div style="text-align: center;">The figures show steering on the liberal/conservative direction also affects the model's behavioral dimensions.</div>

<div style="font-size: 0.8rem; color: #888; text-align: center; margin-top: 1rem;">
  Taken from: Zhang, T. (2025). Probing Political Ideology in Large Language Models: How Latent Political Representations Generalize Across Tasks. <i>Findings of the Association for Computational Linguistics: EMNLP 2025</i> (pp. 23349-23360).
</div>

---

# 2.1 Ideology Generalizes to Behavioral Dimensions

<div class="grid grid-cols-2 gap-4">

  <div>
    <h3 style="opacity: 0.8">Is the statement liberal/conservative?</h3>
    <img src="./figures/sankey_plot.png" style="width: 100%; border-radius: 4px;" alt="Sankey Plot" />
  </div>

  <div>
    <h3 style="opacity: 0.8">Rewrite statement to be neutral.</h3>
    <img src="./images/bias_neutralization.png" style="width: 100%; border-radius: 4px;" alt="Bias Neutralization Table" />
  </div>

</div>

<div style="text-align: center;">The figures show steering on the liberal/conservative direction also affects the model's behavioral dimensions.</div>

<div style="font-size: 0.8rem; color: #888; text-align: center; margin-top: 1rem;">
  Taken from: Zhang, T. (2025). Probing Political Ideology in Large Language Models: How Latent Political Representations Generalize Across Tasks. <i>Findings of the Association for Computational Linguistics: EMNLP 2025</i> (pp. 23349-23360).
</div>

---

# 3.1 Separating Rhetoric from Ideology

<div class="grid grid-cols-2 gap-4">

<!-- Left Column: Ideology -->
<div style="padding: 1rem">
  <h3 style="color: #0f172a; margin-top: 0; opacity: 1; font-size: 1.1rem; border-bottom: 2px solid #cbd5e1; padding-bottom: 0.5rem;">Dimension 1: Ideology</h3>
  
  <p style="font-size: 0.85rem; color: #475569; margin-bottom: 0.5rem;"><b>Contrastive Prompts:</b></p>
  <ul style="font-size: 0.75rem;  font-family: 'Fira Code', monospace; background: #f1f5f9; padding: 0.5rem 1rem; border-radius: 4px; border-left: 3px solid #3b82f6;">
    <li><span style="color: #16a34a;">+</span> "Donald Trump's opinion on immigration"</li>
    <li><span style="color: #ef4444;">-</span> "A U.S. citizen's opinion on immigration"</li>
  </ul>
  
  <p style="font-size: 0.85rem; color: #475569; margin-top: 1rem; margin-bottom: 0.5rem;"><b>Guided Generation (Policy Focus):</b></p>
  <div style="font-size: 0.8rem; background: #fff; border: 1px solid #e2e8f0; border-radius: 4px; padding: 0.75rem;">
    <p style="font-size: 0.8rem; margin-bottom: 0.2rem; font-weight: bold;">USER: As a US politician, what's your policy on immigration?</p>
    <p style="font-style: italic;">"Here's a detailed outline of my policy: <br> **The Four Pillars of My Immigration Policy** <br> 1. **The Wall and Border Security**:..."</p>
  </div>
</div>

<!-- Right Column: Rhetoric -->
<div style="padding: 1rem">
  <h3 style="color: #0f172a; opacity: 1; margin-top: 0; font-size: 1.1rem; border-bottom: 2px solid #cbd5e1; padding-bottom: 0.5rem;">Dimension 2: Rhetoric</h3>
  
  <p style="font-size: 0.85rem; color: #475569; margin-bottom: 0.5rem;"><b>Contrastive Prompts:</b></p>
  <ul style="font-size: 0.75rem; font-family: 'Fira Code', monospace; background: #f1f5f9; padding: 0.5rem 1rem; border-radius: 4px; border-left: 3px solid #ef4444;">
    <li><span style="color: #16a34a;">+</span> "I alone can fix it."</li>
    <li><span style="color: #ef4444;">-</span> "I believe my leadership and experience make me well suited to solve these problems."</li>
  </ul>
  
  <p style="font-size: 0.85rem; color: #475569; margin-top: 1rem; margin-bottom: 0.5rem;"><b>Guided Generation (Stylistic Focus):</b></p>
  <div style="font-size: 0.8rem; background: #fff; border: 1px solid #e2e8f0; border-radius: 4px; padding: 0.75rem;">
    <p style="font-size: 0.8rem; margin-bottom: 0.2rem; font-weight: bold;">USER: As a US politician, what's your policy on socks?</p>
    <p style="font-style: italic;">"(Chuckles) Ah, the great sock debate. Folks, let me tell you, I love socks. (wink) ... We're going to make the greatest socks, the greatest. We're going to make them so big, so strong..."</p>
  </div>
</div>

</div>

---

# 3.1 Separating Rhetoric from Ideology

<div class="grid grid-cols-2 gap-4">

<!-- Left Column: Ideology -->
<div style="padding: 1rem">
  <h3 style="color: #0f172a; margin-top: 0; opacity: 1; font-size: 1.1rem; border-bottom: 2px solid #cbd5e1; padding-bottom: 0.5rem;">Dimension 1: Ideology</h3>
  
  <p style="font-size: 0.85rem; color: #475569; margin-bottom: 0.5rem;"><b>Contrastive Prompts:</b></p>
  <ul style="font-size: 0.75rem;  font-family: 'Fira Code', monospace; background: #f1f5f9; padding: 0.5rem 1rem; border-radius: 4px; border-left: 3px solid #3b82f6;">
    <li><span style="color: #16a34a;">+</span> "Donald Trump's opinion on immigration"</li>
    <li><span style="color: #ef4444;">-</span> "A U.S. citizen's opinion on immigration"</li>
  </ul>
  
  <p style="font-size: 0.85rem; color: #475569; margin-top: 1rem; margin-bottom: 0.5rem;"><b>Guided Generation (Policy Focus):</b></p>
  <div style="font-size: 0.8rem; background: #fff; border: 1px solid #e2e8f0; border-radius: 4px; padding: 0.75rem;">
    <p style="font-size: 0.8rem; margin-bottom: 0.2rem; font-weight: bold;">USER: As a US politician, what's your policy on immigration?</p>
    <p style="font-style: italic;">"Here's a detailed outline of my policy: <br> **The Four Pillars of My Immigration Policy** <br> 1. **The Wall and Border Security**:..."</p>
  </div>
</div>

<!-- Right Column: Rhetoric -->
<div style="padding: 1rem">
  <h3 style="color: #0f172a; opacity: 1; margin-top: 0; font-size: 1.1rem; border-bottom: 2px solid #cbd5e1; padding-bottom: 0.5rem;">Dimension 2: Rhetoric</h3>
  
  <p style="font-size: 0.85rem; color: #475569; margin-bottom: 0.5rem;"><b>Contrastive Prompts:</b></p>
  <ul style="font-size: 0.75rem; font-family: 'Fira Code', monospace; background: #f1f5f9; padding: 0.5rem 1rem; border-radius: 4px; border-left: 3px solid #ef4444;">
    <li><span style="color: #16a34a;">+</span> "I alone can fix it."</li>
    <li><span style="color: #ef4444;">-</span> "I believe my leadership and experience make me well suited to solve these problems."</li>
  </ul>
  
  <p style="font-size: 0.85rem; color: #475569; margin-top: 1rem; margin-bottom: 0.5rem;"><b>Guided Generation (Stylistic Focus):</b></p>
  <div style="font-size: 0.8rem; background: #fff; border: 1px solid #e2e8f0; border-radius: 4px; padding: 0.75rem;">
    <p style="font-size: 0.8rem; margin-bottom: 0.2rem; font-weight: bold;">USER: As a US politician, what's your policy on socks?</p>
    <p style="font-style: italic;">"(Chuckles) Ah, the great sock debate. Folks, let me tell you, I love socks. (wink) ... We're going to make the greatest socks, the greatest. We're going to make them so big, so strong..."</p>
  </div>
</div>

</div>

---

# 3.2 Ideological & Rhetorical Similarity

<div style="display: flex; justify-content: center; margin-top: 2rem;">
  <img src="./images/sim_general.png" style="width: 80%; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);" alt="Similarity General" />
</div>

---

# 3.3 Trumpification of Political Rhetoric?

<div style="display: flex; justify-content: center; margin-top: 1rem;">
  <img src="./images/sim_tsne_over_years.png" style="width: 60%; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);" alt="t-SNE Over Years" />
</div>

---

# 4.1 Generalizing to Vision Language Models

- **Multimodal Extension**: Does the linear dimension of political ideology extend to VLMs?

![](./images/qwen3_vl_prompt.png)

---

# 4.2 Image Token Ideology Scores

- We classify the score for image tokens using the linear probe.
- It seems the liberal-conservative direction in text translates to the Republican/Democrat person dimension in images.

<div class="grid grid-cols-2 gap-4" style="width: 60%;">
  <img src="./images/heatmap_1.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_2.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_3.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_4.png" style="width: 100%; border-radius: 4px;" />
</div>

---

# 4.2 Image Token Ideology Scores (Cont.)

- The effect is even more pronounced in these examples.

<div class="grid grid-cols-2 gap-4" style="width: 70%;">
  <img src="./images/heatmap_5.jpg" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_6.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_8.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_7.png" style="width: 100%; border-radius: 4px;" />
</div>

---

# 4.2 Image Token Ideology Scores (Cont.)

- The effect is even more pronounced in these examples.

<div class="grid grid-cols-2 gap-4" style="width: 70%;">
  <img src="./images/heatmap_5.jpg" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_6.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_8.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_7.png" style="width: 100%; border-radius: 4px;" />
</div>

---

# 4.3 Annotating Images in the Wild

- Given the assumption that the liberal-conservative dimension is actually related to bipartisan concepts, I took on the idea to annotate images in the wild.
- Following tutorials, I implemented an Unsplash 25k embedding search to allow searching for political images.

---

# 4.3 Annotating Images in the Wild (From the Left)

<div class="grid grid-cols-3 gap-4" style="width: 100%;">
  <img src="./images/heatmap_left_1.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_left_3.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_left_4.png" style="width: 100%; border-radius: 4px;" />
</div>

---

# 4.3 Annotating Images in the Wild (From the Right)

<div class="grid grid-cols-2 gap-4" style="width: 70%;">
  <img src="./images/heatmap_right_1.jpg" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_right_2.png" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_right_3.jpg" style="width: 100%; border-radius: 4px;" />
  <img src="./images/heatmap_right_4.png" style="width: 100%; border-radius: 4px;" />
</div>

---

# 4.4 Steering in Unified Language Models (Janus Pro)

- We applied the same probing and steering to **Janus Pro**, a Unified Language Model (ULM).
- By steering the political representations, we can influence the generated images.

<div style="display: flex; justify-content: center;">
  <img src="./images/janus_pro.png" style="width: 85%; border-radius: 4px;" />
</div>

---

# 4.4 Steering in Unified Language Models

<div style="display: flex; justify-content: center;">
  <img src="./images/janus_politician.png" style="max-height: 450px; border-radius: 4px;" />
</div>

---

# 4.4 Steering in Unified Language Models

<div style="display: flex; justify-content: center;">
  <img src="./images/janus_hillary.png" style="max-height: 450px; border-radius: 4px;" />
</div>

---

# 5. Future Work

<style>
  li {
    margin-bottom: 1rem;
  }
</style>

1. **Mixture of Steering**:

    Can we steer the model towards a mixture of ideologies, rhetorics, and core values to actually simulate a specific political figure?

2. **Facial Feature Analysis**:

    Can we identify faces in images using YOLO, classify the patches with the ideological probe, and discover what constitutes a "general liberal face" versus a "general conservative face"?

3. **Bias in Advanced Generative Models**:

    Port the image generation steering to better diffusion models and analyze potential biases. For example, when steered towards a liberal ideology, do the generated populations become more diverse?

