It’s this part of the book that deals with the biggest issue associated with LLMs i.e. Hallucinations.
A jargon sometime back, GenAI had such an impact that ‘hallucination’ became the word of the year
in 2023 by the Cambridge Dictionary. This chapter deals with:
What are hallucinations?
Why do LLMs hallucinate?
How to deal with hallucinations using LangChain?
## What are Hallucinations?
Hallucinations in the context of artificial intelligence often refer to situations where a model generates content that is not accurate or is seemingly made up. It can involve the model "imagining"
details not present in the input data or generating responses that are not grounded in reality.

For example: Suppose you have a conversational AI designed to answer questions about historical facts. 
You asked the following question:

"Who was the first president of the United States?"

In a non-hallucinating response, the AI would correctly provide information like "George Washington"
as the answer. However, in a hallucination scenario, the AI might generate an inaccurate response
like:

"The first president of the United States was Benjamin Franklin."

If you closely notice, the response is syntactically correct but factually wrong. So if you’re ignorant and go into copy-paste mode, this can be problematic. 
Check this fascinating case where a lawyer used ChatGPT to prepare for a case, only to realize it hallucinated and generated fake cases that never existed.

This is very similar to when you go to an exam hall, see the question paper and when you don't know
the answer, you make things up!
But a more complex question,

## Why do LLMs Hallucinate?

Taking a step back, we must understand how LLMs work. They don’t have brains like we do. They just predict the next token given a previous sequence of tokens and input. So, in all, even an LLM
doesn’t know the final answer until the last word is predicted. Eventually, if some facts aren’t available with it (the LLM isn’t trained on that data), the probability of other, closer events/words
may become higher. If you have worked with ChatGPT extensively, when it hallucinates, it doesn’t give a very off-beat answer like ‘President of India is Salman Khan’ but would be mentioning closer
entities. In this case, it can be some former President of India or other political leaders but not actors or people from other fields. This is because given the input and predicted sequence till now,
the probability of semantically similar entities increases. There can be many reasons why LLMs

hallucinate, the major ones being:
#### 1. Limited Contextual Understanding:
LLMs may lack a deep contextual understanding. This limited understanding can result in the model producing hallucinatory content.
#### 2. Incomplete or Noisy Training Data: 
Hallucinations often stem from incomplete or noisy training data. In such a case, the model may generate realistic-sounding but incorrect output.
#### 3. Pattern-Based Generation: 
LLMs might prioritize learned patterns over factual accuracy, especially when faced with ambiguous or complex prompts. This pattern-based generation can
contribute to the model producing outputs that alter facts in a seemingly realistic manner.
#### 4. Biases in Training Data: 
The presence of biases in the training data can influence how LLMs generate content, potentially leading to altering facts to align with biased perspectives.
Now that we know hallucinations in quite some detail, time to know different ways to handle them
using LangChain. For this, LangChain has special chains called LLMCheckersChain and
LLMSummarizationCheckerChain. Let’s have a brief around these special chains first before

#### 1. LLMCheckerChain:
This chain is more like a Fact-checking chain that tells you whether the input is factually correct. So if you ask it ‘We celebrated the 500th birthday of my Father’, the
chain should output: This isn’t possible as a human’s lifespan can’t be 500 years.
#### 2. LLMSummarizationChain:
Going a step ahead of LLMCheckerChain, this helps you to rewrite your input with correct information/facts and not just tell you whether the input is right or
wrong. So, if you input the wrong rules of a game say cricket, this chain will automatically correct the wrong facts in the output.
