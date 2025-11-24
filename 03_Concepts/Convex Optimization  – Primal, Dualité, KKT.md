
# Convex Optimization – Primal, Dualité, KKT  
tags: #optimization #convex #lagrangian #kkt  
date: {{date}}

---

# 1. Objectif général de l’optimisation convexe

Un problème d’optimisation général s’écrit :

$$
\begin{aligned}
\min_x\quad & f(x) \\
\text{s.c.}\quad & g_i(x)\le 0,\quad i=1,\dots,m \\
               & h_j(x)=0,\quad j=1,\dots,p
\end{aligned}
$$

- **$f(x)$** = fonction objectif  
- **$g_i(x)$** = contraintes d’inégalité  
- **$h_j(x)$** = contraintes d’égalité  
- Le but est de trouver un **$x$** réalisable qui minimise $f(x)$.

---

# 2. Domaine et faisabilité

On définit :

- Le **domaine du primal** :
  $$
  \text{dom}(f) \cap \bigcap_{i=1}^m \text{dom}(g_i)
  $$

- L’ensemble des **points réalisables (feasible set)** :
  $$
  \mathcal{F}_{\text{primal}}
  = \{x \mid g_i(x)\le 0,\ \ h_j(x)=0 \}
  $$

---

# 3. Pourquoi la convexité est essentielle ?

Si **f** est convexe et les contraintes définissent un ensemble convexe, alors :

### Proposition :
> *Tout minimum local est un minimum global.*

En effet, pour tout $x^*\in \mathcal{F}$ :
$$
f(x) \ge f(x^*)
$$
dans un voisinage ⇒ cela reste vrai partout dans l’ensemble.

La convexité garantit donc :
- pas de minima locaux "trompeurs",
- convergence des algorithmes.

---

# 4. Résolution algorithmique : descente

Dans tes notes :

> “Find Δx (descent direction)”

Méthode standard :

1. **Trouver une direction de descente**  
   $$
   \nabla f(x)^T \Delta x < 0
   $$

2. **Choisir un pas** α
   $$
   x_{\text{new}} = x + \alpha \Delta x
   $$

3. Répéter tant que la condition d'arrêt n’est pas satisfaite.

---

# 5. Lagrangien : outil indispensable pour mélanger contraintes et objectif

Tes notes manuscrites entrent ensuite dans la partie la plus importante :

> “Lagrangian allows us to mix primal and dual”

Le **Lagrangien** du problème primal est :

$$
\mathcal{L}(x,\lambda,\nu)
= f(x)
+ \sum_{i=1}^m \lambda_i g_i(x)
+ \sum_{j=1}^p \nu_j h_j(x)
$$

où :
- $\lambda_i \ge 0$ : multiplicateurs (inégalités)
- $\nu_j$ : multiplicateurs libres (égalités)

---

# 6. Fonction duale

La fonction duale est définie par :

$$
h(\lambda,\nu)=\inf_{x\in \text{dom}} \mathcal{L}(x,\lambda,\nu)
$$

### Points fondamentaux :

- **h est concave**, même si f ne l’est pas.
- Pour tout $(\lambda,\nu)$ dualement faisable :
  $$
  h(\lambda,\nu)\le p^*
  $$
  où $p^*$ = valeur optimale du primal.

Cela s’appelle la **borne duale**.

---

# 7. Problème dual

On construit alors le problème dual :

$$
\begin{aligned}
\max_{\lambda,\nu}\quad & h(\lambda,\nu) \\
\text{s.c.}\quad & \lambda_i \ge 0
\end{aligned}
$$

Le primal → minimise f(x)  
Le dual → maximise une **borne inférieure** de f(x).

Le lien est :

$$
d^* \le p^*
$$

C’est la **faible dualité** (weak duality).

---

# 8. Forte dualité & KKT

Tes notes disent :

> “certificate of optimality”,  
> “gap = 0”,  
> “KKT → strong duality”.

### Écart de dualité :

$$
\text{gap}(x,\lambda,\nu)
= f(x) - h(\lambda,\nu)
$$

Si le gap est nul → on a atteint la solution exacte.

### Conditions KKT (pour convexité + contraintes régulières)

Les KKT sont :

1. **Stationnarité**
   $$
   \nabla f(x^*)
   +\sum_{i=1}^m \lambda_i^* \nabla g_i(x^*)
   +\sum_{j=1}^p \nu_j^* \nabla h_j(x^*)
   = 0
   $$

2. **Primalement faisable**
   $$
   g_i(x^*)\le 0,\qquad h_j(x^*)=0
   $$

3. **Dualement faisable**
   $$
   \lambda_i^* \ge 0
   $$

4. **Complémentarité**
   $$
   \lambda_i^* g_i(x^*) = 0
   $$

→ si une contrainte n’est pas active (strictement < 0), son λ vaut 0.  
→ si une contrainte est active (=0), son λ peut être > 0.

### Résultat crucial :
> Si le primal est convexe et qu’un triplet $(x^*,\lambda^*,\nu^*)$ satisfait KKT  
> alors  
> **x\*** est optimal primal et **(λ\*,ν\*)** optimal dual.

---

# 9. Exemple de géométrie : plus grand disque dans un polytope

Tes notes montrent un exemple :

> “Find largest ball inside constraints”,  
> “Ax ≤ b”,  
> “maximize r”.

Problème :

On veut trouver le centre $c$ et le rayon $r$ de la plus grande boule $B(c,r)$ contenue dans un ensemble :

$$
Ax \le b.
$$

Pour que la boule soit incluse :  

$$
a_i^T c + r \|a_i\| \le b_i
$$

Donc :

$$
r \le \frac{b_i - a_i^T c}{\|a_i\|}
$$

Finalement :

$$
\max_{c,r}\quad r
$$

sous :

$$
a_i^T c + r\|a_i\| \le b_i.
$$

→ Ceci est un **programme linéaire** (si $\|a_i\|$ est constant).

Tes notes montrent ensuite l’algorithme logiciel classique :
1. construire le problème,
2. résoudre,
3. tracer,
4. analyser les variables duales (qualitative variables).

---

# 10. Résumé visuel des relations

**Primal** minimise :  
$$p^* = \min f(x)$$  

**Dual** maximise :  
$$d^* = \max h(\lambda,\nu)$$  

Toujours :  
$$d^* \le p^*$$  
(faible dualité)

Si KKT satisfaites (convexe) :  
$$d^* = p^*$$  
(forte dualité)

---

