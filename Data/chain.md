### chain
LangChain has a ‘chain’ in its name because of the Chains module. So you can understand its
importance. This chapter is a crucial one as in the upcoming chapters, we will be using many chain
objects.

Chains can be considered as short programs written around LLMs to execute some complex tasks.
It can chain multiple different components like 3rd party tools, python codes, other LangChain
modules like prompt or output parsers, etc. with an LLM or even another LLM with an LLM to get to
the final output. For example: Assume you wish to create a comic using LLMs. Now this is quite
feasible but will include a few steps at a very minimal:
1. Using an LLM and input topic, generate a structure.
2. Write each chapter using the LLM.
3. Generate images.
4. Design a cover page.
5. Save everything in a folder as files.
   
This looks cumbersome. No? Even if you’re using LLMs, a lot of code is required around LLMs to
create a comic creator pipeline. Now, if we have a chain for comic creation, this step would have
been just a one-step task i.e. give input to this chain and your comic is ready.
LangChain provides several pre-defined chains ranging from NLP tasks like Summarization to
Auto-SQL query generators making our lives a lot easier. One thing to remember is chains are quite
restrictive as well. Hence a chain designed for automatic NER tasks would require specifications in
a particular format and are not flexible. So if you try using a NER chain for something else, it will
surely break. Enough of discussions, let’s have a few demos to get a feel.
### LLMChain
 this one chain is prevalent across tutorials. Hence really important. An LLMChain in LangChain is a foundational component that adds basic functionality around LLMs. It
serves as a chain that wraps an LLM to provide additional capabilities such as prompt formatting, input/output parsing, handling conversations and more. LLMChain is widely utilized throughout
LangChain, not only as a standalone object but also in other chains and agents. The core idea behind LangChain is the ability to "chain" together different components and the LLMChain plays a
crucial role in enabling advanced use cases around the LLMs.
