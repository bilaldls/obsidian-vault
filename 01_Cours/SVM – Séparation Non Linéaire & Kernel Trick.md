
---

# 1. Limite du SVM linéaire

Un SVM linéaire cherche un séparateur du type :

$$
f(x)=\langle w,x\rangle + b
$$

Cela fonctionne **uniquement si les classes sont séparables dans l’espace original**  
(celui où vivent les points $x \in \mathbb{R}^d$).

Mais si les données sont comme ceci :

- un cercle rouge entouré d’un anneau bleu,
- un motif « échiquier » alterné,
- des frontières tordues,

**aucun hyperplan ne peut les séparer.**

→ Il faut une stratégie pour **créer un séparateur non linéaire.**

---

# 2. Idée clé : mesurer la similarité entre points

Tes notes disent :

> “a · b is a similarity measure”  
> “similarity matrix : $G_{ij} = y_i y_j \langle u_i, u_j \rangle$”  
> “kernel = similarity”

La **similarité** entre deux points $x_i$ et $x_j$ est souvent mesurée par le produit scalaire :

$$
\langle x_i , x_j \rangle
$$

Mais si les données sont non linéairement séparables, ce produit scalaire ne suffit plus.

On veut une **autre mesure de similarité**, plus flexible, qui puisse capturer des motifs non linéaires.

---

# 3. L’idée géniale : changer d’espace (feature map)

On suppose qu’il existe une application :

$$
\phi : \mathbb{R}^d \rightarrow \mathcal{H}
$$

où $\mathcal{H}$ est un **espace de Hilbert** (potentiellement très grand, voire infini).

Dans cet espace transformé, les données deviennent séparables :

$$
k(x_i, x_j) = \langle \phi(x_i), \phi(x_j) \rangle_{\mathcal{H}}
$$

Cela signifie :

- On **ne calcule jamais $\phi(x)$ explicitement**,
- On calcule **directement le produit scalaire dans le nouvel espace**,
- Ce produit scalaire est appelé **noyau** (kernel).

C’est le **kernel trick**.

---

# 4. Kernel Trick : remplacer le produit scalaire

Dans le SVM du cas linéaire, le dual contient :

$$
G_{ij} = y_i y_j \langle x_i, x_j \rangle
$$

Dans le cas non linéaire, on remplace simplement :

$$
\langle x_i, x_j \rangle \quad \rightarrow \quad K(x_i, x_j)
$$

où :

$$
K(x_i, x_j) = \langle \phi(x_i), \phi(x_j) \rangle_{\mathcal{H}}
$$

**On ne calcule plus jamais $\phi$**.  
On ne manipule que **K**.

---

# 5. Exemples de noyaux vus dans tes notes manuscrites

### 5.1. Noyau polynomial
$$
K(x, x') = (\langle x, x'\rangle + 1)^p
$$

→ Permet de capturer des frontières **courbes**.

---

### 5.2. Noyau Gaussien / RBF (Radial Basis Function)

Tes notes écrivent :

> “k(u, v) = exp( − ||u − v||² )”

La vraie formule est :

$$
K(x, x') = \exp\!\left(-\frac{\|x-x'\|^2}{2\sigma^2}\right)
$$

Ce noyau est **le plus utilisé** car il permet de séparer presque n’importe quelle structure :

- Cercles
- Spirales
- Taches arbitraires

**Intuition :**

- 1 si les points sont très proches → “très similaires”
- 0 s’ils sont loin

Il crée naturellement des frontières courbes complexes.

---

### 5.3. Noyau sigmoïdal (liens avec réseaux de neurones)

$$
K(x, x') = \tanh(\alpha \langle x, x' \rangle + c)
$$

Ce noyau imite le comportement d’un neurone.

---

# 6. Le dual du SVM non linéaire (rappel simplifié)

Primal identique au SVM linéaire → mais dual exprimé en termes de noyaux :

$$
\max_{\lambda} 
\quad -\frac12 \sum_{i,j} \lambda_i \lambda_j y_i y_j K(x_i,x_j)
\quad + \sum_i \lambda_i
$$

avec

$$
\lambda_i \ge 0, \qquad \sum_i \lambda_i y_i = 0
$$

Les **support vectors** = ceux où $\lambda_i > 0$.

---

# 7. Séparateur non linéaire final

La fonction de décision devient :

$$
f(x)=\sum_{i \in SV} \lambda_i y_i K(x_i, x) + b.
$$

**Important :**

- On n’a **pas de $w$ explicite**.
- Tout se fait via les **noyaux**.

---

# 8. Intuition géométrique

Tes notes manuscrites écrivent :

> “What if similarity in first space can be written as a dot product in another space ?”

Explication :

- Dans $\mathbb{R}^d$, les données ne sont pas séparables.
- Mais **il existe un espace transformé** où elles le sont.
- Le kernel donne accès à cet espace **sans jamais le calculer**.

Le séparateur devient une surface très courbe dans l’espace original.

---

# 9. Étapes SVM non linéaire (résumé clair)

1. On choisit un **kernel** $K$  
2. On remplace tous les $\langle x_i, x_j\rangle$ par $K(x_i,x_j)$  
3. On résout le dual du SVM  
4. On trouve les $\lambda_i$  
5. Les vecteurs avec $\lambda_i>0$ = **support vectors**  
6. Le classifieur final :  

$$
f(x)=\sum_{i \in SV} \lambda_i y_i K(x_i,x) + b
$$

---

# 10. Ce qu'il faut ABSOLUMENT retenir

- Le kernel est une **similarité avancée**.
- Le kernel trick évite de calculer les features complexes.
- Le RBF peut séparer presque tout.
- Les SV déterminent entièrement le modèle.
- Plus les données sont non linéaires, plus un SVM RBF fonctionne bien.

---
