# A Survey of Instruction tuning for LLMs

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

## Instruction Tuning for NLP tasks

Licenses for using OpenAI product to generate data: [Prohibit developing models that cmpete with OpenAI](https://openai.com/policies/terms-of-use).

[Learning from Task Descriptions](https://aclanthology.org/2020.emnlp-main.105/)
  * Date: 2020
  * In-context tuning or not: No
  * Base model: T5-11B
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting):
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 


[Cross-Task Generalization via Natural Language Crowdsourcing Instructions (Also called Natural instructions: benchmarking generalization to new tasks from natural language instructions)](https://aclanthology.org/2022.acl-long.244/) **(Natural Instruction)**
  * Date: 04/2021
  * In-context tuning or not: Yes (including positive and negative examples also an explanation of the negative examples)
  * Base model: BART
  * Resource of instruction data: Existing QA-based NLP datasets + human subtask and subtask instruction annotation.
  * Amount of instruction data (after augmenting):61 subtasks, e.g. qustion generation, answer generation, classification.. 193k instances
  * Tested on multiple NLP tasks: The test split of the annotated data
  * Offering data or data-collection tool: Data
  * Licenses: Haven't checked


[Finetuned Language Models are Zero-Shot Learners](https://openreview.net/forum?id=gEZrGCozdqR) **(FLAN2021)** 
  * Date: 09/2021
  * In-context tuning or not: No
  * Base model: LaMDA-PT 137B
  * Resource of instruction data: 62 NLP text datasets in 12 tasks
  * Amount of instruction data (after augmenting): Unknown
  * Tested on multiple NLP tasks: Test on each of the tasks when trained on the rest 11 tasks
  * Offering data or data-collection tool: All NLP datasets used in the study are open-sourced.
  * Licenses: Depends on diffenernt datasets.


[MULTITASK PROMPTED TRAINING ENABLES ZERO-SHOT TASK GENERALIZATION](https://openreview.net/pdf?id=9Vrb9D0WI4) **(P3)** also known as **T0**
  * Date: 10/2021
  * In-context tuning or not: No
  * Base model: T5 11B and 3B
  * Resource of instruction data: Existing NLP datasets on Multi-choice QA, Closed-Book QA, Extractive QA, Sentiment, Topic Classification, Structure-To-Text, Summarization, Praphrase Identification.
  * Amount of instruction data (after augmenting): Not sure
  * Tested on multiple NLP tasks: Sentence Competion, Natural Language Inference, Coreference Resolution, Word Sense Disambiguation, and BIG-Bench Hard.
  * Offering data or data-collection tool: All NLP datasets used in the study are open-sourced.
  * Licenses: Depends on diffenernt datasets.


[Super-NaturalInstructions: Generalization via Declarative Instructions on 1600+ NLP Tasks](https://aclanthology.org/2022.emnlp-main.340/) **(SuperNI)**
  * Date: 04/2022
  * In-context tuning or not: Yes (including positive and negative examples also an explanation of the negative examples, same as natural instructions)
  * Base model: Tk-Instruct (11B)
  * Resource of instruction data: existing NLP datasets + human subtask and subtask instruction annotation.
  * Amount of instruction data (after augmenting): 76 exisiting NLP tasks, 1616 subtasks
  * Tested on multiple NLP tasks: Splits from the annotated data
  * Offering data or data-collection tool: Data
  * Licenses: Unknown


[Scaling Instruction-Finetuned Language Models](https://arxiv.org/pdf/2210.11416.pdf) and 
[The Flan Collection: Designing Data and Methods for Effective Instruction Tuning](https://arxiv.org/pdf/2301.13688.pdf) **(FLAN 2022)**
  * Date: 12/2022 and 04/2023
  * In-context tuning or not: No
  * Base model: T5 and PaLM in different size (10B to 540B)
  * Resource of instruction data:
    - Muffin: 62 tasks in FLAN2021 + 26 tasks including dialouge data and program synthesis data (introduced in this work)
    - T0-SF: 193 tasks = T0 (P3) - the ones covered by Muffin
    - NIV2: 1554 tasks from Super-naturalInstruction
  * Amount of instruction data (after augmenting): unknown, 473 datasets, 146 task categories, 1836 tasks
  * Tested on multiple NLP tasks:
    - MMLU: example questions from 57 tasks
    - BBH: 23 tasks from BIG-Bench
    - TyDiQA: QA benchmarks across 8 languages
    - MGSM: multilingual benchmakr of math work problems manually translated into 10 languages
  * Offering data or data-collection tool: All NLP datasets used in the study are open-sourced.
  * Licenses: Depends on diffenernt datasets.  


## Instruction Tuning for general usage

[Self-Instruct: Aligning Language Models with Self-Generated Instructions](https://arxiv.org/abs/2212.10560) :white_check_mark:
  * Date: 12/2022
  * In-context tuning or not: No
  * Base model: GPT-3 175B (text-davinci-001)
  * Resource of instruction data: 
    - 175 human-written self-instruct seeds
    - Automatic augmentation using text-davinci-001
  * Amount of instruction data (after augmenting): 52K instcution with 82K input-output
  * Offering data or data-collection tool: Both
  * Tested on multiple NLP tasks:
      - SuperNaturalInstruction NLP testset 119 tasks with 100 instances in each task.
  * Licenses: Apache-2.0 license (End-users can utilize the Apache 2.0 license in any commercially licensed software or enterprise application for free. However, Apache trademarks must not be used in the licensed proprietary software or any of the software's legal or organizational documentation.)

[LIMA: Less Is More for Alignment](https://arxiv.org/pdf/2305.11206.pdf) :question:
  * Date: 05/2023
  * In-context tuning or not: No
  * Base model: LLaMA-65B
  * Resource of instruction data: 
    - Stack Exchanges
    - wikiHow
    - Pushshift Reddit
    - Super-Natural Instructions
    - Humman annotated data
  * Amount of instruction data (after augmenting): 1000
  * Offering data or data-collection tool: Unclear
  * Tested on multiple NLP tasks:
    - author collected data + instructions generated from AskReddit
  * Licenses: Unclear

[SAIL: Search-Augmented Instruction Learning](https://arxiv.org/abs/2305.15225) :white_check_mark:
  * Date: 05/2023
  * Base model: LLaMA-7B
  * Resource of instruction data: 
    - Existing instuction datasets Alpaca
    - Searching engines: DuckDuckGo, and BM25 Wikipedia retriever
  * Amount of instruction data (after augmenting): roughly 52K * 5
  * Tested on multiple NLP tasks: Yes
  * Offering data or data-collection tool: Tool
  * Licenses: [GNU General Public License v3.0](https://github.com/facebookresearch/llama/blob/main/LICENSE) Software under the GPL may be run for all purposes, including commercial purposes and even as a tool for creating proprietary software, such as when using GPL-licensed compilers. Users or companies who distribute GPL-licensed works (e.g. software), may charge a fee for copies or give them free of charge.

[Training language models to follow instructions with human feedback](https://arxiv.org/abs/2203.02155)(ChatGPT)
  * Date: 04/2023
  * In-context tuning or not: No
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses:
    
[Language models are few-shot learners](https://arxiv.org/pdf/2005.14165.pdf) (GPT-3)
  * Date: 04/2023
  * In-context tuning or not: No
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses:
  

## Knowledge Distillation

[Sequence-Level Knowledge Distillation](https://aclanthology.org/D16-1139.pdf)

[Alpaca](https://crfm.stanford.edu/2023/03/13/alpaca.html) :x:
  * Date: 2023
  * In-context tuning or not: No
  * Base model: LLaMA-7B
  * Resource of instruction data: 
    - 175 human-written self-instruct seeds
    - Automatic augmentation using text-davinci-003
  * Amount of instruction data (after augmenting): 52K
  * Offering data or data-collection tool: Both
  * Tested on multiple NLP tasks: No
  * Licenses: Alpaca is intended and licensed for research use only. The dataset is CC BY NC 4.0 (allowing only non-commercial use) and models trained using the dataset should not be used outside of research purposes. The weight diff is also CC BY NC 4.0 (allowing only non-commercial use).

[LaMini-LM: A Diverse Herd of Distilled Models from Large-Scale Instructions](https://arxiv.org/abs/2304.14402) :x:
  * Date: 04/2023
  * In-context tuning or not: No
  * Base model: Smaller scaled models (61M to 1.5B) (T5 all sizes, Flan-T5 all sizes, Cereberas-GPT all sizes, GPT-2 all sizes, GPT-Neo)
  * Resource of instruction data: 
    - Existing instuction datasets (self-instuct, P3, FLAN, Alpaca)
    - Automatic instruction augmentation using ChatGPT (gpt-3.5-turbo)
    - Automatic topic augmentation using WikiPedia
  * Amount of instruction data (after augmenting): 2.58M
  * Tested on multiple NLP tasks: 15 diverse NLP tasks, covering QA, sentiment analysis, paraphrase identification, natural language inference, coreference resolution, word sense disambiguation, and sentence completion
  * Offering data or data-collection tool: Data
  * Licenses:
    - Code: Apache-2.0 license (End-users can utilize the Apache 2.0 license in any commercially licensed software or enterprise application for free. However, Apache trademarks must not be used in the licensed proprietary software or any of the software's legal or organizational documentation.)
    - Data: CC BY NC 4.0 (allowing only non-commercial use)


## Others

[Fine-tuned Language Models are Continual Learners](https://aclanthology.org/2022.emnlp-main.410/)
  * Base model: T0
  * Aim at reducing catastrophic forgetting.

[MetaICL: Learning to learn in context.](https://aclanthology.org/2022.naacl-main.201.pdf)
  * Date: 04/2023
  * In-context tuning or not: No
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[ConTinTin: Continual Learning from Task Instructions](https://aclanthology.org/2022.acl-long.218/)
  * Date: 04/2023
  * In-context tuning or not: No
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

[OpenAssistant Conversations - Democratizing Large Language Model Alignment](https://arxiv.org/pdf/2304.07327.pdf)
  * Base model: 
  * Resource of instruction data: 
  * Amount of instruction data (after augmenting)
  * Tested on multiple NLP tasks:
  * Offering data or data-collection tool: 
  * Licenses: 

[Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback](https://arxiv.org/abs/2204.05862)

[StackLLaMA: A hands-on guide to train LLaMA with RLHF](https://github.com/huggingface/blog/blob/main/stackllama.md)

