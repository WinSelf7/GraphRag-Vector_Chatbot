<h1 align="center">ChatPDF</h1>

<div align="center">
  <a href="https://github.com/shibing624/ChatPDF"></a>

  <h3>RAG-based Knowledge Retrieval and Q&A with Local LLM</h3>

  <p>
    <a href="https://github.com/shibing624/ChatPDF/blob/main/LICENSE">
      <img alt="License" src="https://img.shields.io/github/license/shibing624/ChatPDF" />
    </a>
    <a href="https://gradio.app/">
      <img alt="Base" src="https://img.shields.io/badge/Base-Gradio-fb7d1a?style=flat" />
    </a>
  </p>

  <p>Answer questions based on your own files · Open-source models · Local LLM deployment</p>

  <p>
    <img alt="Animation Demo" src="https://github.com/shibing624/ChatPDF/blob/main/docs/snap.png" width="860" />
  </p>
</div>

---

## 📖 Introduction

- This project implements a **lightweight GraphRAG**:
  - Supports **`local` mode** for graph-based retrieval Q&A
  - Supports OpenAI API, DeepSeek API, Ollama API, and can be extended to more LLMs
  - Embedding support: OpenAI, text2vec, Hugging Face, sentence-transformers
  - Asynchronous development with concurrent API requests
- Compatible with multiple open-source LLMs (Qwen, DeepSeek, etc.)
- Supports multiple file formats: PDF, DOCX, Markdown, TXT
- **RAG Accuracy Optimization**
  - Chinese chunk splitting optimized for mixed-language documents
  - Enhanced embeddings using sentence-level vectors
  - BM25 + lexical similarity + semantic similarity weighting
  - Reranker module for improved candidate selection (`rerank_model_name_or_path`)
  - Context expansion for matched chunks (`num_expand_context_chunk`)
  - RAG model customization with support for 200k context length
- Web UI built with **Gradio**, supporting streaming conversations

---

## 🧠 Architecture

<p align="center">
  <img src="https://github.com/shibing624/ChatPDF/blob/main/docs/chatpdf.jpg" width="860" />
</p>

---

## 🚀 Usage

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

💡 If you're on Windows, using WSL (Linux) is recommended.
If CUDA is not installed and you don't want CPU-only mode, install CUDA first.

### Run RAG Example

```shell
CUDA_VISIBLE_DEVICES=0 python rag.py
```

output:

```
prompt: Based on the information below, answer the user’s question using professional knowledge. Respond in Simplified Chinese.

Known content:
[1]	 "ReferencesPeter F Brown, John Cocke, Stephen A Della Pietra, Vincent J Della Pietra, Fredrick Jelinek, John DLafferty, Robert L Mercer, and Paul S Roossin. A statistical 
[2]	 "Let be an encoder that infers the content zfor a given sentence xand a styley
...

问题:
自然语言中的非平行迁移是指什么？

---
回答:
自然语言中的非平行迁移是指在文本生成任务中，我们只能假设访问到非平行或单语的文本数据。这类任务包括翻译和摘要，其中所有问题都涉及这类任务。 
['[1]\t "ReferencesPeter F Brown, John Cocke, Stephen A Della Pietra, Vincent J Della Pietra, Fredrick Jelinek, John DLafferty, Robert L Mercer, and Paul S Roossin. A statistical approach to machine translation.Computational linguistics 
'[2]\t "LetE:X\x02Y!Z be an encoder that infers the content zfor a given sentence xand a styley, andG:Y\x02Z!X be a generator that generates a sentence xfrom a given style yand contentz.EandGform an auto-encoder ', 
...
]
```

### Launch Gradio Web UI

```shell
python webui.py
```

Then open http://localhost:8082  in your browser.

### GraphRAG Example
> [!TIP]
>
>  **Please set OpenAI API key in environment: `export OPENAI_API_KEY="sk-..."`.** 
>
> If you don't have LLM key, check out this [graphrag._model.py](https://github.com/shibing624/ChatPDF/blob/main/graphrag/_model.py#L120) that using `ollama` .

```shell
python graphrag_demo.py
```

- [shibing624/MedicalGPT](https://github.com/shibing624/MedicalGPT)：

MedicalGPT
 — Train your own GPT model, including:

Incremental pretraining

Supervised fine-tuning

RLHF (reward modeling & reinforcement learning)

DPO (direct preference optimization)

