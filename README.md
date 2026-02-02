# Spring AI Ollama Hugging Face Integration

This project demonstrates the simplest integration of Spring AI with Ollama, leveraging Hugging Face GGUF models for both chat completion and embedding tasks.

This is the first step in my quest to gain knowledge about building AI applications, with RAG, MCP and agentic workflows, using Spring AI.

## Overview

Ollama now supports all [GGUF](https://github.com/ggerganov/ggml/blob/master/docs/gguf.md) models from Hugging Face, allowing access to over 45,000 community-created models through [Spring AI's Ollama](https://docs.spring.io/spring-ai/reference/api/chat/ollama-chat.html) integration, runnable locally.

## Prerequisites

- Java 25
- [Ollama](https://ollama.com/download) installed on your system

## Setup

### Versions
- Maven 3.9.12
- Spring AI 2.0.0-M2

### Notes
- `spring.ai.ollama.chat.options.model` and `spring.ai.ollama.embedding.options.model` are used to set the Hugging Face GGUF model names following the naming convention: `hf.co/{username}/{repository}`.
- Models chosen are [Qwen3-8B-GGUF](https://huggingface.co/Qwen/Qwen3-8B-GGUF) and [Qwen3-Embedding-8B-GGUF](https://huggingface.co/Qwen/Qwen3-Embedding-8B-GGUF).
- `spring.ai.ollama.chat.options.think-option` does not work. Spring throws a missing converter exception and attempts to create a custom converter result in sending the `think` property twice to Ollama, which rejects it with an `HTTP 400` error. More about thinking configuration on [Spring AI official docs](https://docs.spring.io/spring-ai/reference/2.0/api/chat/ollama-chat.html#_thinking_mode_reasoning).
- Properties `spring.ai.ollama.chat.options.temperature`, `spring.ai.ollama.chat.options.top-p`, `spring.ai.ollama.chat.options.top-k`, `spring.ai.ollama.chat.options.min-p` and `spring.ai.ollama.chat.options.presence-penalty` are configured according to the best practices section on Hugging Face's model card.  
- The `spring.ai.ollama.init.pull-model-strategy=always` enables automatic model pulling. For production, it's recommended to pre-download the models to avoid delays.

## References
- [Based on Spring's blog post](https://spring.io/blog/2024/10/22/leverage-the-power-of-45k-free-hugging-face-models-with-spring-ai-and-ollama)
- [GGUF docs](https://huggingface.co/docs/hub/gguf)
- [Spring AI Ollama Chat](https://docs.spring.io/spring-ai/reference/2.0/api/chat/ollama-chat.html)
- [Spring AI Ollama Embedding](https://docs.spring.io/spring-ai/reference/2.0/api/embeddings/ollama-embeddings.html)

