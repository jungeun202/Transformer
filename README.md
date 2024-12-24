# Transformer

## Architecture Overview
![image](https://github.com/user-attachments/assets/1fe551ec-0135-47c5-9f26-0184360c31e6) <br />
<sub>The  encoder-decoder structure of the Transformer architecture, taken from “Attention Is All You Need“</sub>

---

### 1. **Input Representation**
- **Token Embeddings:**  
  The input tokens (words or subwords) are transformed into dense vectors that capture their semantic meanings. <br />
  The input embeddings are projected into three spaces using learned weight matrices.
  - Query (Q): What we’re trying to understand (a vector for each token).
  - Key (K): Encodes the importance or "features" of all tokens for comparison.
  - Value (V): The information we want to aggregate or transform (associated with K).
- **Positional Encoding:**  
  Since the Transformer does not inherently model sequence order, positional encoding is added to the embeddings to encode the order of the tokens.

---

### 2. **Encoder**
The encoder consists of a stack of **N identical layers**, with each layer containing the following components:

#### **Multi-Head Self-Attention Mechanism**
- Allows each token to focus on other tokens in the input sequence.
- Captures dependencies between tokens, irrespective of their distance in the sequence.

#### **Feed-Forward Neural Network (FFN)**
- Applies a non-linear transformation to each token individually.

#### **Layer Normalization and Residual Connections**
- Improves stability and helps mitigate vanishing gradient issues.

---

### 3. **Decoder**
Similar to the encoder, the decoder also consists of **N identical layers** but includes additional mechanisms:

#### **Masked Multi-Head Self-Attention**
- Ensures the model does not "peek" ahead during training by masking future tokens.

#### **Encoder-Decoder Attention**
- Focuses on relevant outputs from the encoder to generate the next token in the sequence.

#### **Feed-Forward Neural Network (FFN)**
- Functions similarly to the encoder's FFN.

---

### 4. **Attention Mechanism**
Attention is a weighted computation based on the similarity between query (\(Q\)) and key (\(K\)) vectors. It is defined as:

$`\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V`$

- $`(Q, K, V)`$: Learned projections of the input.
- $`d_k`$: Dimensionality of the key vectors.
  
This similarity measures "how much one token should focus on another."

---

### 5. **Multi-Head Attention**
- Employs multiple attention heads to capture various relationships within the sequence.
- Each head computes attention independently, and the results are concatenated.

---

### 6. **Positional Encoding**
- Provides information about the token order using sinusoidal functions.
- Added to the token embeddings to preserve the sequential structure of the input.

---

### 7. **Output Linear Layer and Softmax**
- **Linear Layer:** Maps decoder outputs to a vector space corresponding to the vocabulary size.  
- **Softmax Layer:** Converts the vector into probabilities for the next token prediction.

---

This architecture forms the backbone of many state-of-the-art natural language processing (NLP) models, enabling them to perform a variety of tasks effectively.
