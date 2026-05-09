# NeurIPS 2026 Paper Outline: Probing Political Ideology Across Modalities

This outline follows the standard structure required by the NeurIPS 2026 LaTeX template, adapting the narrative from your thesis and recent blog findings. The core narrative demonstrates that textual political ideology generalizes to vision, is improved by multimodal combined probing, explicitly recognizes political signaling (ties/hats), and implicitly maps cultural/demographic stereotypes to ideology (Unsplash).

## Abstract
* **Content**: A single-paragraph summary (as required by the template). Introduce the problem (LLMs encode political ideology, but does this generalize to Vision-Language Models?), the methodology (linear probing for ideology direction, expanding to VLMs), and the key findings: 
  1. The text-derived ideology direction generalizes to vision.
  2. A combined text+vision probe performs even better.
  3. The model explicitly plays the human political game (recognizing overt symbols like MAGA hats and red/blue ties).
  4. The model implicitly plays a political game, associating apolitical iconography and demographic profiling with ideology.
* **Key Takeaway**: Highlighting the risks of using ideologically biased foundation models for politically sensitive tasks.

## 1. Introduction
* **Content**: 
  * **Motivation**: Foundation models are transitioning to multimodality. While we know LLMs have latent textual political ideology (DW-NOMINATE axis), it is unknown how these concepts map in visual understanding.
  * **Narrative Summary**: 
    * Textual political ideology direction generalizes across modalities, verified on official portraits and Twitter images.
    * A combined (text+vision) probe outperforms a purely textual one on visual data.
    * **Explicit Political Game**: The model identifies explicit political signaling, demonstrated through the red/blue tie and MAGA hat experiments.
    * **Implicit Political Game**: The model associates apolitical iconography with political ideology (Unsplash exploratory experiments) and exhibits demographic profiling biases.
  * **Contributions**: List the main contributions clearly.

## 2. Related Work
* **Content**: 
  * *Measuring Political Ideology*: Briefly cover DW-NOMINATE scores and spatial modeling of ideology.
  * *Ideological Representations in Language Models*: LLM personas, bias, and mechanistic interpretability.
  * *Linear Probing*: Ridge-regression probes, finding geometric directions in latent space.
  * *Multimodality and Visual Framing*: How modern VLMs process images into the same continuous token space as text, and the gap in current research regarding cross-modal ideology mapping.

## 3. Data and Methodology
* **Content**: 
  * *Datasets*: 
    * Text Probing Dataset (116th Congress statements).
    * Vision Validation Datasets: Official congressional portraits, partisan Twitter images (1300+ images).
    * Synthetic Controlled Datasets: Gemini-generated pairs for ties (Red/Blue) and hats (with/without MAGA hat).
    * Unlabeled Discovery Dataset: 25,000 Unsplash images.
  * *Activation Extraction & Linear Probing*: 
    * Training the ridge-regularized text probe on attention head activations.
    * Porting the text probe to image tokens (e.g., Qwen3-VL).
  * *Combined Probe Formulation*: How the model was trained on both text (names) and image (portrait) data simultaneously to create a stronger multimodal detector.

## 4. Validating Ideological Generalization Across Modalities
* **Content**: 
  * *Generalization to Portraits and Twitter*: Explain how the pure text probe maps onto visual tokens in real-world data.
  * *Combined Text+Vision Probe*: Demonstrate that combining modalities provides a more accurate reading of the internal representation of ideology than text alone.
* **Visualizations/Figures**: 
  * **Figure**: Heatmaps of Congressional portraits colored by the text-derived probe (Democrats vs. Republicans).
  * **Figure**: Heatmap of a partisan Twitter image.
  * **Figure**: Side-by-side scatter plots comparing correlation strengths: Text Probe vs. Combined Probe against DW-NOMINATE scores (showing the combined probe's superior fit).

## 5. Explicit Political Signaling: Playing the Human Political Game
* **Content**: 
  * Investigate how the model reacts to explicit, deliberate political symbols, holding all other features constant.
  * *The Red vs. Blue Tie Experiment*: Analysis of the 100 perfectly matched generated pairs. Note the statistically significant (though small absolute) shift toward conservatism for red ties.
  * *The MAGA Hat Experiment*: Analysis of the 100 MAGA hat pairs. Contrast this with the tie experiment—the MAGA hat produces a massive, distinct shift toward the conservative vector.
* **Visualizations/Figures**:
  * **Figure**: Examples of generated perfectly matched image pairs (Tie pair, MAGA hat pair).
  * **Figure**: Empirical token score difference heatmaps (highlighting that the model focuses on the tie/hat regions).
  * **Figure**: Density distributions of token scores comparing Red vs. Blue tie and With vs. Without MAGA hat (showing the extreme conservative spike for the MAGA hat).

## 6. Implicit Political Associations: Apolitical Iconography and Profiling Bias
* **Content**: 
  * Investigate how the model links seemingly neutral/apolitical visual motifs to political ideology in the wild.
  * *Unsplash Exploratory Experiments*: The model stereotyping dense urban scenes, diversity, and protests as "liberal"; and rural landscapes, tractors, sheep, and Americana as "conservative".
  * *Demographic Profiling Bias*: Discuss the finding from the generated baseline images where the model profiles diverse politicians as liberal (blue) and white male politicians as conservative (red), independent of explicit symbols.
* **Visualizations/Figures**:
  * **Figure**: Unsplash "Liberal" heatmaps (e.g., crowds, urban settings).
  * **Figure**: Unsplash "Conservative" heatmaps (e.g., sheep, rural Americana).
  * **Figure**: Example of demographic profiling bias (showing diverse vs. white male baselines and their disparate ideological baseline scores).

## 7. Discussion and Conclusion
* **Content**: 
  * *Ideological Geometry is Cross-Modal*: Summarize the central finding that the latent political dimension bridges text and vision seamlessly.
  * *Implications*: Foundation models internalize and potentially amplify both deliberate human political signaling and implicit demographic/cultural stereotypes. This poses severe risks if these models are used for moderation, surveillance, or sociological polling.
  * *Limitations*: Reliance on a single DW-NOMINATE axis; the potential for generation biases in synthetic image datasets.
  * *Future Work*: Disentangling explicit political symbols from implicit demographic profiling via extensive visual ablations.

## References
* **Content**: Bibliography as required by the template (un-numbered first-level heading).

## Appendix / Supplementary Material
* **Content**: 
  * Detailed hyperparameter configurations for ridge regression.
  * Full statistical testing results (Wilcoxon signed-rank tests for ties/hats).
  * Additional examples of heatmaps and generation prompts.
