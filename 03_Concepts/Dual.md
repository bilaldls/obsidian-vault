But : résoudre un problème d'optimisation 

$min_x (f_0(x))$  sous contraintes : $f_i(x)\leq0$ 

# Concept: Dual

### 1. Définition intuitive

Chaque $λ_i$  ajoute une “pénalité” pour violer la contrainte.  

Tu choisis les $λ$ pour rendre ces pénalités **aussi sévères que possible** tout en gardant une borne inférieure valide.

C’est comme choisir les meilleurs poids pour dire :
> “Toute solution du primal doit coûter au moins $g(λ)$.”

Et tu cherches le _meilleur_ de ces certificats.
### 2. Définition formelle (si applicable)


on rappel :  $L(x,λ)=f_0​(x)+∑​λ_i​f_i​(x)$        $λ_i​≥0$  

ce qui nous permet de définir : 

$g(λ)=inf_x(​L(x,λ))$


- Le **Dual** cherche une meilleure borne inférieure sur ce minimum 


 **Pourquoi on fait une inf sur $x$ ?**

Parce que :
- $L$ est une fonction **affine en $λ$**
- donc **facile à maximiser** une fois l’inf fait sur $x$
- et parce que $g(λ)$ est toujours [[concave]] même si le [[Primal]] ne l'est pas. 

Cette concavité garantit que le dual est un **problème simple**, “sans pièges locaux”.


### 3. Contextes où il apparaît
- Cours :
  - [[Maths_SVME]]
  
- Axes transverses :
  - [[]]

### 4. Liens avec d'autres concepts
- [[Primal]]
- 

### 5. Exemple simple
- 

### 6. Remarques perso / pièges
- 
