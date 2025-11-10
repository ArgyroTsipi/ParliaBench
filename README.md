
# ParliaBench  
### AI Benchmark for Parliamentary Speech Generation and Evaluation using 'ParlaMint-GB'

**ParliaBench** is an open research benchmark for evaluating large language models (LLMs) on structured political discourse generation.  
It processes the *'ParlaMint-GB'* corpus (UK Parliament), fine-tunes multiple transformer-based models, generates synthetic parliamentary speeches, and evaluates their linguistic, semantic, and ideological alignment through a comprehensive suite of metrics.

---

## Abstract  

**ParliaBench** introduces a reproducible framework for analyzing how fine-tuned generative models emulate patterns of parliamentary speech.  
The project evaluates models’ ability to reproduce political discourse styles and party-specific rhetoric by integrating preprocessing, model fine-tuning, speech generation, and multi-dimensional evaluation.

The pipeline includes:  
1. **Corpus preprocessing** — parsing and structuring *ParlaMint-GB* XML debates with full speaker metadata, integrates political orientation and classifies speeches with EuroVoc topics using Kevlar
2. **Model training** — fine-tuning LLMs using parameter-efficient 4-bit quantized adapters  
3. **Controlled generation** — producing speeches conditioned on political party, political orientation, house, section, and topic  
4. **Comprehensive evaluation** — combining linguistic, semantic, and embedding-based metrics  

This work contributes toward reproducible evaluation of **AI-based political discourse simulation** and **socially grounded text generation**.

---

## Repository Structure  


---

## Models  

All models were fine-tuned using **Unsloth’s parameter-efficient 4-bit LoRA** implementation for reduced memory footprint and reproducibility.

| Model | Identifier | Parameters | Framework |
|-------|-------------|-------------|------------|
| LLaMA-3.1 | `unsloth/Meta-Llama-3.1-8B-bnb-4bit` | 8B | Hugging Face / Unsloth |
| Mistral | `unsloth/mistral-7b-v0.3-bnb-4bit` | 7B | Hugging Face / Unsloth |
| Gemma-2 | `unsloth/gemma-2-9b-bnb-4bit` | 9B | Hugging Face / Unsloth |
| Yi-1.5 | `unsloth/Yi-1.5-6B-bnb-4bit` | 6B | Hugging Face / Unsloth |
| Qwen2 | `unsloth/Qwen2-7B-bnb-4bit` | 7B | Hugging Face / Unsloth |

---

## Evaluation Metrics  

**ParliaBench** integrates a *multi-layered evaluation framework* assessing linguistic fluency, semantic coherence, diversity, and ideological alignment.

### 1. Linguistic Diversity
| Metric | Description | Interpretation |
|---------|--------------|----------------|
| **Distinct-n (1, 2, 3, 4)** | Ratio of unique n-grams to total tokens | ↑ Higher → greater lexical diversity |
| **Self-BLEU** | Similarity among generated samples | ↓ Lower → more diverse speech patterns |
| **Perplexity** | Fluency measure based on model confidence | ↓ Lower → smoother language generation |

### 2. Semantic Quality
| Metric | Description | Interpretation |
|---------|--------------|----------------|
| **MoverScore** | Semantic distance using word mover distance | ↑ Higher → closer to human reference speeches |
| **BERTScore** | Contextual similarity using transformer embeddings | ↑ Higher → stronger semantic fidelity |
| **GRUEN** | Evaluates grammar, coherence, and fluency | ↑ Higher → more human-like readability |

### 3. Ideological and Political Alignment
| Metric | Description | Purpose |
|---------|--------------|----------|
| **Party Alignment Embeddings** | Cosine similarity of party-specific embeddings | Measures consistency with political party |
| **Political Spectrum Embeddings** | Positioning along a left–right ideological axis, embeddings for cos similarity | Measures consisyency with political orientation |
| **LLM-as-a-Judge** | MODEL-based comparative scoring of coherence and realism | Provides qualitative evaluation |

---

