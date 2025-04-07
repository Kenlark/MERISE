# MPD (Modèle Physique de Données)

---

L'étape de création du **MPD** permet de construire la structure finale de la base de données avec les différents liens entre les éléments qui la composent.

- Les **entités** se transforment en **tables**.
- Les propriétés se transforment en **champs** (ou **attributs**).
- Les propriétés se trouvant au milieu d'une relation génèrent une nouvelle table ou glissent vers la table adéquate en fonction des cardinalités de la relation.
- Les **identifiants** se transforment en clés et se retrouvent soulignés. Chaque table dispose d'au minimum une **clé primaire**.
- Les relations et les cardinalités se transforment en champs parfois soulignés : il s'agit de créer des **clés étrangères** reliées à une **clé primaire** dans une autre table.

C'est aussi à cette étape que les aspects performances sont pris en compte. La construction d'index ou des opérations de "_dénormalisation_" faciliteront la rapidité de la base de données mais pourront aussi entraîner des incohérences.
