
# Concept: Attention Mechanism

### 1. Définition intuitive
- 

### 2. Définition formelle


Let $\mathbf{X} \in \mathbb{R}^{t \times d}$ be a sequence of $t$ tokens of dimension $d$.  

Let $\mathbf{W}_q, \mathbf{W}_k, \mathbf{W}_v \in \mathbb{R}^{d \times d}$ three matrices of parameters.  

Self-Attention is computed following this formula:

  

$$

\operatorname{SelfAttention}(\mathbf{X}) =

\operatorname{Softmax}\!\left(

\frac{\mathbf{X}\mathbf{W}_q \, (\mathbf{X}\mathbf{W}_k)^{\top}}{\sqrt{d}}

\right)\mathbf{X}\mathbf{W}_v

$$

  

- $\mathbf{Q} = \mathbf{X}\mathbf{W}_q$ are the **Queries**.  

- $\mathbf{K} = \mathbf{X}\mathbf{W}_k$ are the **Keys**.  

- $\mathbf{V} = \mathbf{X}\mathbf{W}_v$ are the **Values**.  

- $\operatorname{Softmax}\!\left(\frac{\mathbf{Q}\mathbf{K}^{\top}}{\sqrt{d}}\right) \in (0,1)^{t \times t}$ is the score matrix.  

- Attention has a **quadratic complexity** with respect to the number of tokens. It cannot be computed for long sequences.
### 3. Contextes où il apparaît
- Cours :
  - [[Artificial Neural Networks & Deep Learning]]
  - [[Natural Language Processing Introduction]]
  - 
  
- Axes transverses :
  - [[]]

### 4. Liens avec d'autres concepts
- [[]]
- 

### 5. Exemple simple
- 

### 6. Remarques perso / pièges
- 
