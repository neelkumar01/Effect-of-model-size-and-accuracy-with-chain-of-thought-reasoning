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

Q: A bakery bakes 48 cookies and packs them equally into 6 boxes. They sell 3 boxes. How many cookies are left?
A: First, find cookies per box: 48 ÷ 6 = 8 cookies per box. They sell 3 boxes, so cookies sold = 3 × 8 = 24. Cookies remaining = 48 - 24 = 24. The answer is 24.

Q: Maria earns 15 dollars per hour. She works 6 hours on Saturday and 4 hours on Sunday. How much does she earn in total?
A: Saturday earnings = 15 × 6 = 90 dollars. Sunday earnings = 15 × 4 = 60 dollars. Total earnings = 90 + 60 = 150. The answer is 150.

Q: A train has 9 compartments. Each compartment seats 40 passengers. If 187 passengers are on board, how many seats are empty?
A: Total seats = 9 × 40 = 360. Empty seats = 360 - 187 = 173. The answer is 173.

Q: A farmer has 5 fields. Each field produces 120 kg of wheat. He sells 200 kg and stores the rest. How many kg does he store?
A: Total wheat = 5 × 120 = 600 kg. Stored wheat = 600 - 200 = 400. The answer is 400.

Q: Riya saves 25 dollars every week. After 8 weeks, she spends 60 dollars on a book. How much does she have left?
A: Total saved = 25 × 8 = 200 dollars. After spending = 200 - 60 = 140. The answer is 140.

Q: A school has 4 classrooms. Each classroom has 5 rows of desks, and each row has 6 desks. How many desks are there in total?
A: Desks per classroom = 5 × 6 = 30. Total desks = 4 × 30 = 120. The answer is 120.

Q: A store had 500 bottles of water. They received a new shipment of 3 crates, each holding 80 bottles. They then sold 240 bottles. How many bottles remain?
A: Bottles from shipment = 3 × 80 = 240. Total after shipment = 500 + 240 = 740. Remaining = 740 - 240 = 500. The answer is 500.

Q: Three friends split a restaurant bill of 96 dollars equally. Each then leaves a 5 dollar tip. How much does each person pay in total?
A: Each person's share of bill = 96 ÷ 3 = 32 dollars. Each person's total = 32 + 5 = 37. The answer is 37.
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
