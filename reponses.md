# Partie 2
- Question : relancez terraform plan. Pourquoi annonce-t-il « No changes » alors que vous venez de créer deux objets ?
```
    La commande 'terraform plan' affiche 'no changes' car on a définit dans notre main.tf que l'image ne doit être reconstruite que si le filesha1 est modifié or en réappliquant notre terraform en ne faisant aucune modification, ce filesha restera le même et donc tf ne reconstruira pas l'image donc ne fera aucun changement.
```