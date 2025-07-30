# Transformer Architectures: Encoder-only vs Decoder-only vs Encoder-Decoder
**Professional Cheat Sheet for Modern Generative AI**

---

## What are Encoder and Decoder?

- **Encoder:** Reads and encodes input data into a rich, contextual representation.
- **Decoder:** Generates output data (text, image, etc.) from a representation.

**Memory Trick:** Encoder = "Understands", Decoder = "Speaks/Generates"

---

## 1. Encoder-Only Models

| Feature         | Description                                                        |
|-----------------|--------------------------------------------------------------------|
| Structure       | Stack of encoder blocks (no decoder).                              |
| Usage           | Input understanding, embedding, extraction, classification         |
| Famous Models   | BERT, RoBERTa, DistilBERT, ELECTRA                                 |
| Practical Use   | Semantic search, information extraction, classification, QA retrieval |
| Diagram         |                                                                    |

```
[Input Text] → [Encoder Blocks] → [Rich Contextual Representation]
```

---

## 2. Decoder-Only Models

| Feature         | Description                                                        |
|-----------------|--------------------------------------------------------------------|
| Structure       | Stack of decoder blocks (no encoder).                              |
| Usage           | Text generation, auto-completion, creative writing                 |
| Famous Models   | GPT-2/3/4, Llama, Gemini, Mistral                                  |
| Practical Use   | Chatbots, code generation, content writing, story completion       |
| Diagram         |                                                                    |

```
[Prompt/Start Text] → [Decoder Block 1] → ... → [Decoder Block N] → [Generated Text]
```
*(Output is generated token by token, using previous outputs as context)*

---

## 3. Encoder-Decoder (Seq2Seq) Models

| Feature         | Description                                                        |
|-----------------|--------------------------------------------------------------------|
| Structure       | Stack of encoders, stack of decoders (with cross-attention).       |
| Usage           | Input-output transformation (translation, summarization, captioning)|
| Famous Models   | T5, BART, MarianMT, original Transformer (Vaswani et al.)          |
| Practical Use   | Google Translate, text summarization, generative QA, data-to-text  |
| Diagram         |                                                                    |

```
[Input Text] → [Encoder Blocks] → [Context]
                                ↓
                         [Decoder Blocks] → [Output Text]
```

---

## Connection to Classic Models

| Model         | Encoder Part | Decoder Part | Similar to Transformer?       |
|---------------|-------------|-------------|-------------------------------|
| Autoencoder   | Yes         | Yes         | Encoder-Decoder (not for text)|
| VAE           | Yes         | Yes         | Encoder-Decoder               |
| GAN           | No          | Yes         | Generator = Decoder           |
| BERT          | Yes         | No          | Encoder-only                  |
| GPT, Llama    | No          | Yes         | Decoder-only                  |
| T5, BART      | Yes         | Yes         | Encoder-Decoder               |

---

## When to Use Each Type?

| Model Type        | Use When...                                                      |
|-------------------|------------------------------------------------------------------|
| Encoder-only      | Understanding, classification, information extraction            |
| Decoder-only      | Text generation, completion, creative tasks                      |
| Encoder-decoder   | Input-to-output transformation (translate, summarize, QA, caption)|

---

## Real-World Examples

| Model Type        | Famous Model         | Practical Usage                         |
|-------------------|---------------------|------------------------------------------|
| Encoder-only      | BERT, RoBERTa       | Semantic search, document classification |
| Decoder-only      | GPT-3, Llama        | ChatGPT, Copilot, code/email generation  |
| Encoder-decoder   | T5, BART, MarianMT  | Translation, summarization, Q&A          |

---

## Visual Gallery (ASCII Diagrams)

```
Encoder-Only:      [Input] → [Encoder Stack] → [Representation]
Decoder-Only:      [Prompt] → [Decoder Stack] → [Output...]
Encoder-Decoder:   [Input] → [Encoder] → [Context] → [Decoder] → [Output]
```

---

## Summary Table: Encoder vs Decoder vs Both

| Feature         | Encoder-only | Decoder-only | Encoder-Decoder |
|-----------------|--------------|--------------|-----------------|
| Reads Input?    | Yes          | (Prompt only)| Yes             |
| Generates Output?| No           | Yes          | Yes             |
| Main Task       | Understand   | Generate     | Transform       |
| Examples        | BERT         | GPT, Llama   | T5, BART        |

---

## Why Does This Matter in Generative AI?

- Encoder-only: For understanding or extracting info from text (embedding, search, classification).
- Decoder-only: For generating or continuing text/code (story, chatbot, code generation).
- Encoder-decoder: For mapping input to output (translation, summarization, Q&A).

---

# End of Cheat Sheet
