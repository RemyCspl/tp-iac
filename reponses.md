# Partie 2
- Question : relancez terraform plan. Pourquoi annonce-t-il « No changes » alors que vous venez de créer deux objets ?
```
    Terraform compare la configuration à son état enregistré ; les deux ressources existent déjà et sont conformes, donc il annonce « No changes ».
```

# Partie 3
- Question : seul tp-iac-lb1 publie le port 8080. Quelle ligne de quel fichier en décide ?
```
    Seul tp-iac-lb1 possède un port http 8080 car c'est la seule key de notre variable serveur qui possède une value pour http_port.
```

# Partie 4
-  Question : ouvrez inventory.ini, modifiez un port à la main, puis relancez terraform plan. Que propose Terraform ? Qu'en concluez-vous sur le rôle de ce fichier ? (Faites terraform apply pour le remettre en ordre avant de continuer.)
```
    Terraform propose de rétablir le port attendu. Cela montre que inventory.ini est généré par Terraform et ne doit pas être modifié à la main.
```

# Partie 5
- Question : le module command affiche CHANGED alors qu'un simple cat ne modifie rien. Pourquoi ? Que faudrait-il ajouter dans un playbook pour que ce soit juste ?
```
    command signale CHANGED par défaut, car Ansible ne peut pas savoir si la commande modifie le système. Pour un cat, ajoutez changed_when: false au playbook.
```

# Partie 6
- Question : au deuxième passage, le handler « Redémarrer PostgreSQL » ne s'est pas exécuté. Pourquoi ?
```
    Au deuxième passage, PostgreSQL est déjà configuré : aucune tâche n’a changé, donc aucune n’a notifié le handler. Celui-ci ne redémarre le service qu’après un changement.
```

# Partie 7
- Question : connectez-vous à api1 (ssh -i ~/.ssh/tp_iac_ed25519 -p 2242 -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null ansible@127.0.0.1) et tapez cat /etc/stockline/stockline.env. Que se passe-t-il, et pourquoi est-ce voulu ? (exit pour revenir.)
```
    L’accès au fichier est refusé, car il contient le mot de passe de la base et ses permissions le réservent à l’utilisateur stockline et à root.
```

# Partie 9
- Question : combien de fichiers avez-vous modifiés pour ajouter un serveur ? Faites la liste de tout ce que Terraform puis Ansible ont fait à votre place.
```
    Un seul fichier : terraform/variables.tf a dû être modifié à la main. 
    Terraform a créé le conteneur et mis à jour l’inventaire ; Ansible a configuré api3 et ajouté ce serveur à la configuration nginx.
```