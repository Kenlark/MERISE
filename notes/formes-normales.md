# 📘 Les Formes Normales (1FN, 2FN, 3FN)

Les formes normales permettent de structurer correctement les bases de données relationnelles pour éviter les redondances et incohérences.

---

## 🔹 1FN – Première Forme Normale

> **Une table est en 1FN si chaque case contient une seule valeur "atomique".**

### ✅ À respecter :

- Chaque champ doit contenir **une seule donnée** (pas de listes, pas de tableaux).
- Les valeurs doivent être **indivisibles** (pas de sous-informations cachées).

### 🧠 À savoir :

- Une date ou une adresse IP peuvent sembler composées, mais restent **atomiques** si elles ont un sens global et ne sont pas divisées pour stocker autre chose.
- Exemple de donnée **non atomique** : un numéro de sécurité sociale français (car il cache plusieurs infos : sexe, date de naissance, lieu, etc).

### ❌ Exemple non conforme :

| Nom   | Téléphones             |
| ----- | ---------------------- |
| Alice | 0601020304, 0611223344 |

### ✅ Exemple conforme :

| Nom   | Téléphone  |
| ----- | ---------- |
| Alice | 0601020304 |
| Alice | 0611223344 |

---

## 🔹 2FN – Deuxième Forme Normale

**Une table est en 2FN si elle est en 1FN ET que tous les champs dépendent de toute la clé primaire.**

### ✅ À respecter :

- Si la clé primaire est **composée** (plusieurs colonnes), chaque champ doit dépendre de **toute** la clé, pas d'une partie.

### ❌ Exemple non conforme :

| NumClient | NumProduit | NomClient |
| --------- | ---------- | --------- |
| 1         | 101        | Alice     |

Ici, `NomClient` dépend uniquement de `NumClient`, pas de la combinaison complète (`NumClient`, `NumProduit`).

### ✅ Solution :

Créer deux tables :

- `Client(NumClient, NomClient)`
- `Commande(NumClient, NumProduit)`

---

## 🔹 3FN – Troisième Forme Normale

**Une table est en 3FN si elle est en 2FN ET que tous les champs dépendent directement de la clé primaire (pas via un autre champ).**

### ✅ À respecter :

- Aucun champ ne doit dépendre **d’un autre champ non identifiant**.
- Il ne doit pas y avoir de **dépendance transitive** (A → B → C).

### ❌ Exemple non conforme :

| NumClient | CodePostal | Ville |
| --------- | ---------- | ----- |
| 1         | 75000      | Paris |

Ici, `Ville` dépend de `CodePostal`, pas directement de `NumClient`.

### ✅ Solution :

Créer deux tables :

- `Client(NumClient, CodePostal)`
- `CodePostal(CodePostal, Ville)`

---

## ✅ Résumé des Formes Normales

| Forme | Objectif                           | Ce qu’elle impose                                 |
| ----- | ---------------------------------- | ------------------------------------------------- |
| 1FN   | Éviter plusieurs infos par cellule | Chaque champ contient une seule valeur "atomique" |
| 2FN   | Éviter dépendance partielle        | Chaque champ dépend de **toute** la clé           |
| 3FN   | Éviter dépendance entre champs     | Chaque champ dépend **directement** de la clé     |

---

✅ **Respecter les 3 premières formes normales permet d’avoir une base de données bien structurée, évolutive, sans redondance, et facile à maintenir.**
