---
title: LLM observability and cost management on HPE Private Cloud AI
date: 2026-03-06T06:06:26.225Z
author: Santosh Nagaraj
authorimage: /img/Avatar1.svg
disable: false
---


LLM observability and cost management are *critical for deploying reliable, secure, and financially sustainable AI applications*. By tracking metrics like token usage, latency, and output quality, teams can prevent runaway costs, reduce hallucinations, and ensure regulatory compliance.

[LiteLLM](https://www.litellm.ai/) and [Langfuse](https://langfuse.com/) together *provide a powerful, open-source stack for LLM observability and cost management (tokenomics)*, allowing developers to unify, trace, and monitor API usage across hundreds of models. LiteLLM acts as the proxy/SDK to normalize requests and track usage, while Langfuse records these interactions for detailed analysis of token usage, latency, and costs.

This blog post walks you through deployment and configuration of LiteLLM and Langfuse, on HPE Private Cloud AI. By leveraging these technologies, organizations can perform token-level cost tracking, granular tracing, output streaming and cost analysis of LLMs deployed on HPE Private Cloud AI.

## HPE Private Cloud AI

[HPE Private Cloud AI (HPE PCAI)](https://developer.hpe.com/platform/hpe-private-cloud-ai/home/) offers a comprehensive, turnkey AI solution designed to address key enterprise challenges, from selecting the appropriate LLMs to efficiently hosting and deploying them. Beyond these core functions, HPE Private Cloud AI empowers organizations to take full control of their AI adoption journey by offering a curated set of pre-integrated *NVIDIA Inference Microservices (NIM)* LLMs, along with a powerful suite of AI tools and frameworks for data engineering, analytics, and data science.

HPE Machine Learning Inference Software (MLIS) is an enterprise-grade solution designed to simplify the **deployment, management, and monitoring** of machine learning (ML) models at scale. It specifically targets the complexities of moving models from development into production, with a particular focus on **Large Language Models (LLMs)**. 

HPE Private Cloud AI has pre-integrated NVIDIA NIM LLMs, a suite of AI tools (including HPE Machine Learning Inference Software), and a flexible *Import Framework* that enables organizations to deploy their own applications or third-party solutions, like LiteLLM and Langfuse.

![](/img/screenshot-2026-03-06-121708.png)



## Deploy Langfuse and LiteLLM via Import Framework

1. ### Prepare the Helm charts for Langfuse
2. ### Deploy and configure Langfuse
3. ### Prepare the Helm charts for LiteLLM
4. ### Deploy and configure LiteLLM



## Deploy LLM in HPE MLIS



### Configure LiteLLM



### LLM observability and cost analysis in Langfuse