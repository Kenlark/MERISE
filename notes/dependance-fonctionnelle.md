# 🔗 Dépendance fonctionnelle (DF) – Méthode MERISE

---

## 📘 Définition

Une **dépendance fonctionnelle** signifie qu’un **attribut A permet de déterminer un attribut B**.

Si je connais la valeur de A, alors je connais **une seule valeur possible** pour B.  
Cela s’écrit : **A → B** (on dit "A détermine B")

---

## 🧠 Exemple simple

Table `Client` :

| NumClient | Nom    | Prénom |
| --------- | ------ | ------ |
| 1         | Dupont | Alice  |
| 2         | Martin | Bob    |

Ici :

- `NumClient → Nom` ✅
- `NumClient → Prénom` ✅  
  Le numéro du client détermine **exactement** le nom et le prénom.

❌ Inversement :

- `Nom → NumClient` n’est **pas valide**, car plusieurs clients peuvent avoir le même nom.

---

## ⚙️ Types de dépendances

### ✅ Dépendance fonctionnelle **complète**

Tous les attributs de la clé sont nécessaires pour déterminer un autre attribut.

Exemple : `(NumClient, DateCommande) → MontantCommande`

### ⚠️ Dépendance fonctionnelle **partielle**

Un seul attribut (ou une partie de la clé) suffit à déterminer un autre attribut.

Exemple : `NumClient → NomClient`

👉 Cela viole la **2ème forme normale (2FN)**.

### 🔁 Dépendance **transitive**

Un attribut dépend **indirectement** de la clé.

Exemple :

- `NumCommande → NumClient`
- `NumClient → NomClient`
- Donc : `NumCommande → NomClient` (transitivement)

👉 Cela viole la **3ème forme normale (3FN)**.

---

## 📚 Exemple MERISE

Table `Commande` :

| NumCommande | DateCommande | NumClient | NomClient |
| ----------- | ------------ | --------- | --------- |

Dépendances :

- `NumCommande → DateCommande`
- `NumCommande → NumClient`
- `NumClient → NomClient` (dépendance transitive)

❌ `NomClient` ne dépend **pas directement** de `NumCommande`, donc **la 3FN n’est pas respectée**.

---

## ✅ Utilité des dépendances fonctionnelles

Elles servent à :

- Identifier les **clés primaires**
- Appliquer les **formes normales** (1FN, 2FN, 3FN…)
- Éviter les **redondances**, **incohérences** et **données inutiles**

---

## 📌 Récapitulatif

| Type de dépendance | Définition                                    |
| ------------------ | --------------------------------------------- |
| A → B              | A détermine B                                 |
| Complète           | Tous les attributs de la clé sont nécessaires |
| Partielle          | Une partie de la clé suffit                   |
| Transitive         | Dépendance indirecte via un autre attribut    |

---

Besoin d'un exemple visuel ou MCD/MLD en plus ? Demande-moi !
