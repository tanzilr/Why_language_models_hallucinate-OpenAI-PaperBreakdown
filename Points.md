
## Hallucination - Meaning
A plausible falsehoods, which diminish their utility. This error mode is known as “hallucination,” though it differs fundamentally from the human perceptual experience.


Hallucinations aren’t mysterious: they appear because of statistical pressures. The authors reduce generation to a **binary classification** task (“Is-It-Valid?”) and show a tight link:  generative error rate ≳ 2 × IIV misclassification rate. 

> In short, if a model can’t reliably classify valid vs. invalid strings, it will sometimes generate the invalid ones.

## Reason of hallucination (after pre-training)
Even with **error-free** corpora, minimising cross-entropy pushes calibrated base models to make some errors; many arise where there’s **no learnable pattern** (arbitrary facts like birthdays) or when the model class is **too weak** for the concept.
    
**Singleton rate bound (arbitrary facts)**
For facts that appear only once in training (“singletons”), base models will hallucinate at least at that **singleton fraction** (up to constants). If 20% of birthday facts are singletons, expect ≥~20% hallucination on birthdays.
    
**Other statistical drivers**  
- Poor models -  representational mismatch (e.g., counting letters with tokenisation quirks).  
- Distribution shift - odd or OOD prompts.  
- GIGO - models replicate errors in the data.

## Reason of persistence of hallucinations(after post-training)
Most leaderboards/benchmarks score binary accuracy and give **zero credit for “I don’t know.” That rewards guessing when unsure, so “test-taker” models bluff confidently to win. The authors call this an epidemic of penalising uncertainty.

An "Epidemic" of Misaligned Evaluations. The core issue is that most of the influential benchmarks and leaderboards that the AI community relies on are

Misaligned with the goal of creating trustworthy AI:
- **Model A** is an honest model that says "I don't know" (IDK) when it's uncertain and never hallucinates.
- **Model B** is a guessing model that provides its best guess whenever it's uncertain.
    
## Proposed fix (socio-technical).
Don’t add yet another “hallucination eval.” **Modify mainstream benchmarks** (e.g., SWE-bench, HLE, MMLU-Pro, GPQA) to include **explicit confidence targets** in the instructions (e.g., “answer only if > t confident; wrong answers cost t/(1−t) points”). This rewards abstention when appropriate and shifts incentives away from bluffing.

**Behavioural calibration (what to check).** 
- With explicit thresholds, the optimal strategy across tasks is to answer only when confidence ≥ t, otherwise abstain—a behaviour you can audit by plotting accuracy vs. allowed-confidence thresholds.
- Limits & scope - The framework treats hallucinations as **plausible falsehoods** (not nonsense), applies to **prompted** settings, and notes that RAG/reasoning aren’t panaceas if grading still punishes uncertainty.

If you want, I can turn this into a 1-page slide or a checklist for benchmark redesign (confidence thresholds, abstention handling, reporting behavioural calibration).

## Some Relevant Questions:

**What is base model in this context?**
A base model is the foundational version of a LLM that has just completed the first stage - which is pre-training. Pre-training is creating the base model and post-training is refining the base model.

**How error free data leads to errors and hallucination?**
The distribution of language is initially learned from a corpus of training examples, which inevitably contains errors and half-truths. However, we show that even if the training data were error-free, the objectives optimised during language model training would lead to errors being generated. With realistic training data containing shades of error, one may expect even higher error rates.
