## Effect of Model Size on Accuracy with Few Shot Chain of Thought Reasoning

### Overview

The core idea is that few shot CoT prompting providing a model with a handful of example problems that include intermediate reasoning steps can dramatically unlock a model's problem-solving capability. But the key finding, popularized by Google's 2022 "Chain of Thought Prompting Elicits Reasoning in Large Language Models" paper, is that this ability is not uniformly distributed across model sizes. It appears to be an emergent property: small and medium models show little to no benefit from CoT prompts, while very large models (typically 100B+ parameters) suddenly exhibit strong performance gains



### Models Tested / To be Tested

| Model Name | Parameters |
|---|---|
| Flan-T5 Small | 80M | 
| Flan-T5 Base | 250M | 
| Flan-T5 Large | 780M | 
| Qwen2.5 0.5B | 0.5B | 
| Gemma 2 2B | 2B | 
| LLaMA 3.2 3B | 3B | 
| Phi-3 Mini | 3.8B | 
| Mistral 7B Instruct | 7B | 
| Qwen2.5 7B | 7B | 
| DeepSeekMath 7B | 7B | 
| Qwen2.5-Math 7B | 7B | 

### Dataset — GSM8K

GSM8K (Grade School Math 8K) is a benchmark of 8,500 high-quality, linguistically diverse grade school math word problems, designed to test multi-step arithmetic reasoning.

- Each problem requires 2 to 8 reasoning steps
- Problems are written in natural language
- Widely used to evaluate LLM reasoning capabilities



### Few Shot Examples

Each model was prompted with these few shot examples demonstrating step by step reasoning:

```
Q: Emily has 3 apples. Her friend gives her 2 more. How many apples does Emily have now?
A: Emily starts with 3 apples. Her friend gives her 2 more. So, 3 + 2 = 5. The answer is 5.

Q: A pen costs 2 dollars. John buys 4 pens. How much does he pay?
A: Each pen costs 2 dollars. John buys 4 pens. So, 2 × 4 = 8. The answer is 8.

Q: Jake read 5 pages on Monday and 7 pages on Tuesday. How many pages did he read in total?
A: Jake read 5 pages on Monday and 7 on Tuesday. So, 5 + 7 = 12. The answer is 12.
```



### Results (More coming soon)

| Model | Accuracy (with CoT) |
|---|---|
| Flan-T5 Small | ~2% |
| Flan-T5 Base | ~2% |
| Flan-T5 Large | ~6% |
| Mistral 7B Instruct | ~6% |


### Key Observations

- Chain of Thought Reasoning is only effective for bigger models.

- The model starts to give reasoning steps if input-output chain of thought examples are provided.

- Inspite of using model bigger models upto 7B parameters, accuracy remains low on arithmetic datasets


### Reference research papers

- "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models" - https://arxiv.org/abs/2201.11903
- "Large Language Models are Zero-Shot Reasoners" - https://arxiv.org/abs/2205.11916
