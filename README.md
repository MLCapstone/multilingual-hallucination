# Analyzing LLM Hallucination Mitigation Methods For Low-Resource Languages

## Abstract

This study analyzes the effectiveness of various hallucination mitigation techniques in the generation of multilingual long-form text. Using the Multi-FAct evaluation framework (Shafayat et al. (2024)), the final fact evaluation score is derived from the FActScore metric, which is the percentage of claims in the LLM text that are verified using Wikipedia retrievals. This study evaluates the factuality of the biographies of national leaders produced by a Qwen 8B model. Our analysis performs each hallucination mitigation strategy on high, medium, and low resource languages, specifically English, Hindi, Bengali, and Swahili. We compare a vanilla baseline against two distinct mitigation strategies: Retrieval-Augmented Generation (RAG) and Chain-of-Thought (CoT) prompting. Within RAG, we test two separate sub-strategies: one retrieves information from English Wikipedia while the other retrieves information from the target language Wikipedia. Similarly, for Chain-of-Thought prompting, we test two separate styles: one being Zero-Shot Chain-of-Thought and the other being Plan-and-Solve Chain-of-Thought. The findings of this study aim to clarify the relationship between the availability of linguistic resources and the effectiveness of reasoning-based versus retrieval-based strategies in reducing hallucination.


## Introduction
This codebase contains the code for the paper [Analyzing LLM Hallucination Mitigation Methods For Low-Resource Languages](Capstone_Paper.pdf). This paper was produced as a submission for the Machine Learning Capstone at University of Washington in Spring 2026.

This codebase is extends the [Multi-FAct codebase](https://github.com/sheikhshafayat/multi-fact) which in turn builds heavily on top of the [FActScore codebase](https://github.com/shmsw25/FActScore). Please cite both these original paper too if you find this code useful.

The original Multi-FAct paper is modified to use Qwen-8B for fact generation. The verification pipeline remains identical Multi-FAct which uses Mistral for breaking the long-form text in atomic facts. The Wiki database used as the information source from fact verification is inherited from the FActScore database.

All experiment results reported in Multi-FAct paper are generated using Qwen-8B for biography generation and retrieval + mistral for fact verification.


## Getting Started
The codebase is organized as follows:

- `generated_bios_qwen_baseline/`: contains the baseline biographies used in the paper.
- `generated_bios_qwen_rag/`: contains the RAG aided biographies used in the paper.
- `generated_bios_qwen_CoT/`: contains the CoT aided biographies used in the paper.
- `necessary_dicts/`: contains the necessary dictionaries for the code.
- `factscore.py`: contains the modified code for the FActScore metric.
- `bio_generator.ipynb`: contains the code to generate all bios (baseline, RAG based, and CoT based).
- `evaluation.ipynb`: contains the set-up to calculate FActScores on all biographies after they are translated to English using GPT-4.

