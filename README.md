OpenAI and Gerogia Tech researchers released a paper regarding hallucinations in LLMs. And it was interesting to see their perspective on this. These are just my notes/mindmaps I created to understand it.


As we deploy more and more applications with AI integration, the hallucination results into security implications and risk. Understanding it is first step to managing it.

Few interesting takeaways:

- The way we evaluate AI models with right/wrong scores actually rewards the model for bluffing when they are uncertain, just like a student guessing on a multiple-choice exam to maximise their score

- As a result, we are essentially penalise when a model responds: 'I don't know' and wrong answer are both scored zero. The model takes the probability of being correct when uncertain

- Even if the data is free from errors, but the way natural language is translated into statistical calculation, during training, inevitably produces responses that we can categorise as hallucinations

Original Paper: https://lnkd.in/eMMMaXde
