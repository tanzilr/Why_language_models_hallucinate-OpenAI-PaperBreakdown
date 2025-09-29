# Why Language Models Hallucinate

This repository contains materials related to the paper "Why Language Models Hallucinate" by OpenAI.

## Contents

*   **[why-language-models-hallucinate-by-OpenAI.pdf](why-language-models-hallucinate-by-OpenAI.pdf):** The full paper.
*   **[Points.md](Points.md):** Key takeaways and summary of the paper.
*   **[Why Language Model Hallucinates (Paper by OpenAI).xmind](Why Language Model Hallucinates (Paper by OpenAI).xmind):** A mind map visualizing the concepts in the paper.
*   **[Why Language Model Hallucinates (Paper by OpenAI).png](Why Language Model Hallucinates (Paper by OpenAI).png):** An image of the mind map.

## Summary

This paper argues that language model "hallucination" (generating plausible falsehoods) is a result of statistical pressures during training. The authors frame generation as a binary classification task ("Is-It-Valid?") and show that generation errors are linked to classification errors.

### Key Reasons for Hallucination:

*   **Arbitrary Facts:** For facts that appear only once in the training data ("singletons"), the model is likely to hallucinate.
*   **Model Weaknesses:** The model may not be complex enough to understand certain concepts.
*   **Distribution Shift:** The model may be prompted with out-of-distribution inputs.
*   **Data Errors:** The model replicates errors present in the training data.

### Persistence of Hallucinations:

The paper argues that current evaluation methods reward models for guessing, which encourages "bluffing" and perpetuates hallucinations.

### Proposed Solution:

The authors propose modifying mainstream benchmarks to include confidence targets, which would reward models for abstaining when uncertain.
