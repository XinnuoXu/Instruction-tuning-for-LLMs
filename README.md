# Instuction tuning for LLMs

Language models are pretrained to predict the next token at an incredible scale, allowing them to learn general-purpose representations that can be transferred to nearly any language understanding or generation task. 
To enable this transfer, various methods for aligning language models have thus been proposed, primarily focusing on **instruction tuning** over (instruction, intput, output) triplet datasets.
More recently **reinforcement learning from human feedback (RLHF)**, collected over millions of interactions with human annotators, also has been approved to improve the performance of alignment.
This repo is a literature review for instruction tunning for LLMs.

## Existing LLMs

* [LLaMA](https://arxiv.org/abs/2302.13971)
  - Scales: 7B, 13B, 65B
  - Licenses: [GNU General Public License v3.0](https://github.com/facebookresearch/llama/blob/main/LICENSE) Software under the GPL may be run for all purposes, including commercial purposes and even as a tool for creating proprietary software, such as when using GPL-licensed compilers. Users or companies who distribute GPL-licensed works (e.g. software), may charge a fee for copies or give them free of charge.
* [Chinchilla]
  - Scales: 70B
  - Licenses: 
* [PaLM]
  - Scales: 540B
  - Licenses: 
* [GPT-3]
  - Scales: 175B
  - Licenses: 

## Instruction Tuning

Licenses for using OpenAI product to generate data: [Prohibit developing models that cmpete with OpenAI](https://openai.com/policies/terms-of-use).

[Alpaca](https://crfm.stanford.edu/2023/03/13/alpaca.html) :x:
  * Base model: LLaMA-7B
  * Resource of instruction data: 
    - 175 human-written self-instruct seeds
    - Automatic augmentation using text-davinci-003
  * Amount of instruction data (after augmenting): 52K
  * Offering data or data-collection tool: Both
  * Tested on multiple NLP tasks: No
  * Licenses: Alpaca is intended and licensed for research use only. The dataset is CC BY NC 4.0 (allowing only non-commercial use) and models trained using the dataset should not be used outside of research purposes. The weight diff is also CC BY NC 4.0 (allowing only non-commercial use).

[Self-Instruct: Aligning Language Models with Self-Generated Instructions](https://arxiv.org/abs/2212.10560) :white_check_mark:
  * Base model: GPT-3 175B (text-davinci-001)
  * Resource of instruction data: 
    - 175 human-written self-instruct seeds
    - Automatic augmentation using text-davinci-001
  * Amount of instruction data (after augmenting): 52K instcution with 82K input-output
  * Offering data or data-collection tool: Both
  * Tested on multiple NLP tasks: No
  * Licenses: Apache-2.0 license (End-users can utilize the Apache 2.0 license in any commercially licensed software or enterprise application for free. However, Apache trademarks must not be used in the licensed proprietary software or any of the software's legal or organizational documentation.)

[LIMA: Less Is More for Alignment](https://arxiv.org/pdf/2305.11206.pdf) :question:
  * Base model: LLaMA-65B
  * Resource of instruction data: 
    - Stack Exchanges
    - wikiHow
    - Pushshift Reddit
    - Super-Natural Instructions
    - Humman annotated data
  * Amount of instruction data (after augmenting): 1000
  * Offering data or data-collection tool: Unclear
  * Tested on multiple NLP tasks: No
  * Licenses: Unclear

[LaMini-LM: A Diverse Herd of Distilled Models from Large-Scale Instructions](https://arxiv.org/abs/2304.14402) :x:
  * Base model: Smaller scaled models (61M to 1.5B) (T5 all sizes, Flan-T5 all sizes, Cereberas-GPT all sizes, GPT-2 all sizes, GPT-Neo)
  * Resource of instruction data: 
    - Existing instuction datasets (self-instuct, P3, FLAN, Alpaca)
    - Automatic instruction augmentation using ChatGPT (gpt-3.5-turbo)
    - Automatic topic augmentation using WikiPedia
  * Amount of instruction data (after augmenting): 2.58M
  * Tested on multiple NLP tasks: Yes
  * Offering data or data-collection tool: Data
  * Licenses:
    - Code: Apache-2.0 license (End-users can utilize the Apache 2.0 license in any commercially licensed software or enterprise application for free. However, Apache trademarks must not be used in the licensed proprietary software or any of the software's legal or organizational documentation.)
    - Data: CC BY NC 4.0 (allowing only non-commercial use)

[SAIL: Search-Augmented Instruction Learning](https://arxiv.org/abs/2305.15225) :white_check_mark:
  * Base model: LLaMA-7B
  * Resource of instruction data: 
    - Existing instuction datasets Alpaca
    - Searching engines: DuckDuckGo, and BM25 Wikipedia retriever
  * Amount of instruction data (after augmenting): roughly 52K * 5
  * Tested on multiple NLP tasks: Yes
  * Offering data or data-collection tool: Tool
  * Licenses: [GNU General Public License v3.0](https://github.com/facebookresearch/llama/blob/main/LICENSE) Software under the GPL may be run for all purposes, including commercial purposes and even as a tool for creating proprietary software, such as when using GPL-licensed compilers. Users or companies who distribute GPL-licensed works (e.g. software), may charge a fee for copies or give them free of charge.

[MULTITASK PROMPTED TRAINING ENABLES ZERO-SHOT TASK GENERALIZATION](https://openreview.net/pdf?id=9Vrb9D0WI4)(P3)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[The Flan Collection: Designing Data and Methods for Effective Instruction Tuning](https://arxiv.org/pdf/2301.13688.pdf)(FLAN)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Super-NaturalInstructions: Generalization via Declarative Instructions on 1600+ NLP Tasks](https://aclanthology.org/2022.emnlp-main.340/)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Learning from Task Descriptions](https://aclanthology.org/2020.emnlp-main.105/)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Cross-Task Generalization via Natural Language Crowdsourcing Instructions](https://aclanthology.org/2022.acl-long.244/)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Finetuned Language Models are Zero-Shot Learners](https://openreview.net/forum?id=gEZrGCozdqR)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Training language models to follow instructions with human feedback](https://arxiv.org/abs/2203.02155)(ChatGPT)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Fine-tuned Language Models are Continual Learners](https://aclanthology.org/2022.emnlp-main.410/)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Scaling Instruction-Finetuned Language Models](https://arxiv.org/abs/2210.11416)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[ConTinTin: Continual Learning from Task Instructions](https://aclanthology.org/2022.acl-long.218/)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[InstructDial: Improving Zero and Few-shot Generalization in Dialogue through Instruction Tuning](https://aclanthology.org/2022.emnlp-main.33/)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Crosslingual Generalization through Multitask Finetuning](https://arxiv.org/abs/2211.01786)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 
