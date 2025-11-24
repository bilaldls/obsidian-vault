

---

## 1. Problème de classification linéaire

On dispose d’un ensemble d’apprentissage :

$$
L=\{(x_k, y_k)\}_{k=1}^r, \quad x_k \in \mathbb{R}^d,\ y_k\in\{-1,1\}.
$$

On cherche un **séparateur linéaire** sous la forme :

$$
f(x)=\langle w,x\rangle + b
$$

Le séparateur est la surface de niveau :

$$
S(w,b)=\{x\mid f(x)=0\}=\{x\mid \langle w,x\rangle + b =0\}.
$$

---

## 2. Séparation stricte (cas linéairement séparable)

Si les données sont linéairement séparables, il existe $((w,b))$ vérifiant :

$$
\langle w,x_k\rangle + b \ge 1 \quad \text{si } y_k=1
$$

$$
\langle w,x_k\rangle + b \le -1 \quad \text{si } y_k=-1
$$

Ce qui se réécrit de façon compacte :

$$
y_k(\langle w,x_k\rangle+b)\ge 1.
$$

---

## 3. Marge

Le vecteur \(w\) est orthogonal au plan séparateur.

La **marge** associée à $(S(w,b))$ est :

$$
\text{marge}=\frac{2}{\|w\|}.
$$

Objectif : **maximiser la marge**.

Maximiser $(\frac{2}{\|w\|})$ équivaut à minimiser $(\frac{1}{2}\|w\|^2)$.

---

## 4. Problème Primal (standard)  

D’après la mise sous forme standard fournie dans le cours :

$$
\begin{cases}
\min\limits_{w,b} \quad f_0(w)=\frac{1}{2}\|w\|^2 \\
\text{s.c.}\quad -y_k(\langle w,x_k\rangle + b) + 1 \le 0,\quad k=1,\dots,r
\end{cases}
\tag{Primal}
$$

Sous forme matricielle avec $(a_k = -y_k x_k^T)$ :

$$
Aw - yb + \mathbf{1} \le 0.
$$

---

## 5. Support Vectors (définition)

Définition formelle :

$$
I(SV) = \{k\mid y_k(\langle w,x_k\rangle + b)=1\}.
$$

Ceux qui **saturent** les contraintes.

**Interprétation** :  
Ce sont les seules observations qui influencent le séparateur optimal.

---

## 6. Lagrangien du primal

On introduit les multiplicateurs de Lagrange $(\lambda_k \ge 0)$.

$$
L(w,b,\lambda)=
\frac12 w^T w 
+ \sum_{k=1}^r \lambda_k \big[ (-y_k x_k)^T w - y_k b + 1 \big].
$$

Notations du cours :

- $(A)$ contient les lignes $(a_k=(-y_k x_k)^T)$,
- $(y=[y_1,\dots,y_r]^T)$,
- $(\mathbf{1}=[1,\dots,1]^T)$.

---

## 7. Conditions KKT

$$
\frac{\partial L}{\partial w}=w + A^T\lambda = 0
\quad\Rightarrow\quad
w = -A^T\lambda = \sum_{k=1}^r \lambda_k y_k x_k.
$$

$$
\frac{\partial L}{\partial b} = -\lambda^T y=0
\quad\Rightarrow\quad
\sum_{k=1}^r \lambda_k y_k = 0.
$$

Conditions de complémentarité :

$$
\lambda_k \ge 0,\quad 
\lambda_k[-y_k(\langle w,x_k\rangle+b)+1]=0.
$$

Les **support vectors** sont ceux où $(\lambda_k>0)$.

---

## 8. Problème Dual (cas séparable)

Seuls \(w\) et \(b\) sont éliminés dans la dualité :

$$
g(\lambda)
= -\frac12 \lambda^T (A A^T)\lambda + \mathbf{1}^T\lambda.
$$

Dual :

$$
\begin{cases}
\max\limits_{\lambda} 
\quad -\frac12 \lambda^T (A A^T)\lambda + \mathbf{1}^T\lambda \\
\text{s.c.}\quad \lambda \ge 0,\quad \lambda^T y = 0
\end{cases}
\tag{Dual}
$$

et

$$
w=\sum_{k\in I(\lambda>0)} \lambda_k y_k x_k.
$$

---

## 9. Séparateur final

Le séparateur maximal de marge est :

$$
S(w,b)=\sum_{k\in I(\lambda>0)}\lambda_k y_k \langle x_k, x\rangle + b = 0.
$$

---

## 10. Fonction de décision (prédiction)

Pour un nouvel exemple \(x\) :

$$
f(x)=\sum_{k\in I(\lambda>0)} \lambda_k y_k \langle x_k,x\rangle + b.
$$

Décision :

$$
\text{class}(x)=\text{sign}(f(x)).
$$

---

## 11. Notes manuscrites intégrées (Goodnotes)

Depuis tes notes (Maths For ML) :  
- schémas séparateur, marges, \(H_{+1}\), \(H_{-1}\)  
- rappel que les contraintes donnent :

$$
y_k(\langle w,x_k\rangle+b)=\pm 1.
$$

- dérivation du dual (z = λ)  
- KKT corrects  
- représentateur :

$$
w=\sum \lambda_k y_k x_k.
$$

Tout concorde avec le PDF du prof, tu étais aligné.

---

## 12. Structure mentale : ce qu’il faut retenir

- **But** : maximiser la marge.  
- **Primal** : minimiser $(\|w\|^2/2)$.  
- **Dual** : combinaison linéaire des données.  
- **Seules les données avec $(\lambda_k>0)$** comptent → SV.  
- **Décision** : signe de la somme pondérée.

---


