# Multi-Agent DSPy Research

**Goal:** Learn the [DSPy](https://github.com/stanfordnlp/dspy) framework and test out a multi-agent hypothesis: `In layered LLM agent systems, increasing the supervising agent’s intelligence can lead to lower performance overall.`

If you’ve ever been prompt tuning, asked the model why it made some mistake and got a surprising reason, you’ve stumbled upon my reasoning for testing this out. You (or the hypothesized smarter agent) didn’t fully understand how the less intelligent agent perceived the task. Does closing the intelligence gap create clarity between the two agents that could lead to increased performance?

### Experiement

To test this out, I wanted to create a trivial version of a layered multi-agent system. DSPy, a framework for algorithmically optimizing LM prompts and weights, created an easy way to accomplish that. 
With DSPy, I set up a simple multi-agent scenario where one agent provides instructions (prompts) to another. DSPy creates a framework for algorithmically updating the prompts based off the performance of the current prompt. Using a well-known dataset, I set this experiement up as an LLM classification task to identify the topic from text. I configured the prompting agent to be `gpt-4o` in the first scenario and `gpt-4o-mini` in the second (task agent was `gpt-4o-mini` in both). 

Unfortunately, the experiment (as you can replicate with the provided notebook) does not show improved performance. DSPy does do a great job with optimization, taking the baseline performance from 31% accuracy to 82% accuracy with `gpt-4o`. Swapping out the model with `gpt-4o-mini` leads to 64% accuracy. I guess any communication gap imposed by increasing intelligence does not seem to outweigh the benefits of greater intelligence! (At least with `4o` and `4o-mini` powering our two agents.)
