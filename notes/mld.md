# MLD (Modèle Logique de Données)

---

Le **MLD** est une des dernières étapes proposées et elle permet d'implémenter la base de données en transcrivant le **MCD** en instructions **SQL** adaptées au **SGBDR** prévu. Concrètement, le **MLD** permet de connaître le nombre de tables ainsi que leurs contraintes (liaisons entre tables) à mettre en œuvre dans une base de données relationnelle.

## Comment réaliser un MLD ?

On représente ainsi les données issues de la modélisation **Merise** sous la forme suivante :

- Chaque ligne représente une **table**.
- Toujours le nom de la table qui est écrit en premier.
- Les **champs** sont listés entre parenthèses et séparés par des virgules.
- Les **clés primaires** sont soulignées et placées au début de la liste des champs.
- Les **clés étrangères** sont préfixées par un dièse.
