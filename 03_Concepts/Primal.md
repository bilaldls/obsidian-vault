But : résoudre un problème d'optimisation 

$min_x (f_0(x))$  sous contraintes : $f_i(x)\leq0$ 

# Concept: Primal

### 1. Définition intuitive

-  Le **Primal** cherche une meilleur valeur de $f_0(x)$ en respectant les contraintes
"Trouve moi la meilleure solution admissible"

### 2. Définition formelle (si applicable)

**Chaque contrainte peut donner une “pénalité” à la solution si elle n’est pas satisfaite.**  

On crée donc un **nouveau problème** construit à partir des multiplicateurs de **Lagrange**.

On transforme le problème initial en : 

$L(x,λ)=f_0​(x)+∑​λ_i​f_i​(x)$        $λ_i​≥0$


Puis on regarde : 

$g(λ)=inf_x(​L(x,λ))$

Et on cherche à **maximiser** $g(λ)$.

Autrement dit :

- Le _primal_ cherche une **meilleure valeur de $f_0(x)$** en respectant les contraintes.
    
- Le [[Dual]] cherche une **meilleure borne inférieure** sur ce minimum.
### 3. Contextes où  il apparaît
- Cours :
  - [[Maths_SVME]]
  
- Axes transverses :
  - [[]]

### 4. Liens avec d'autres concepts
- [[Dual]]
- [[KKT]]
- [[Convex Optimization  – Primal, Dualité, KKT]]
- 

### 5. Exemple simple
- 

### 6. Remarques perso / pièges
- 
