
# Concept: Encodeur Block

### 1. Définition intuitive
- 

### 2. Définition formelle (si applicable)

![[Encodeur Architecture.png]]



<div class="side">
  <img src="Encodeur Architecture.png">

  <div class="text">
    <p><strong>Inputs :</strong> one-hot encoding of the sentences. They are represented as a list of indices. </p>
    <p><strong>Input Embedding :</strong> is a linear projection of the inputs. </p>
    <p> <strong> Positional Inputs : </strong> are the one-hot matrix of the token positions to encode their position. They are represented as a list of indices. </p>
	<p><strong> Positional Embedding : </strong> is a linear projection of the positional inputs. </p>
	<p><strong>Multi Head Attention : </strong> layer is an Attention module computed multiple times in parallel.  </p>
	<p><strong> Feed-Forward  </strong>  layer is a linear projection, an activation function (usually GELU) and a second linear projection : (see below) </p>
	<p><strong>  Add & Norm </strong>  are residual connection and a layer normalization module : (see below) </p>
	
  </div>
</div>
**Feed Forward :**

$$\mathbf{X}' = \mathrm{GELU}(\mathbf{X}\mathbf{W}_1 + \mathbf{b}_1)\mathbf{W}_2 + \mathbf{b}_2$$
**Add&Norm :**

$$\mathbf{X}' = \mathrm{LayerNorm}(\mathbf{X} + \mathrm{Attention}(\mathbf{X}))

$$






### 3. Contextes où il apparaît
- Cours :
  - [[Natural Language Processing Introduction]]
  
- Axes transverses :
  - [[]]

### 4. Liens avec d'autres concepts
- [[Transformers]]
- [[Decodeur]]
-  [[One-hot encoding]] 
- 

### 5. Exemple simple
- 

### 6. Remarques perso / pièges
- 
