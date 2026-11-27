# Rendu — Atelier Kubernetes

> Complétez ce fichier au fil de l'atelier, puis faites un commit et un push (voir la section « Rendu » du README).

**Nom / Prénom :**
**Groupe :**

---

## Exercice 1 — Cluster

1. Combien de nœuds affiche `kubectl get nodes` ? Quel est le rôle de chacun ?
>
   On a 3 noeuds , l'un va agir en tant que serveur , deux autres agents.
>
2. Que montre `docker ps` ? Qu'est-ce qu'un « nœud » dans k3d, concrètement ?
>
Docker ps montre les conteneurs qui sont lancés qui font tourner le cluster : On en a 4 <img width="1390" height="297" alt="image" src="https://github.com/user-attachments/assets/da39d9ef-d4cf-48c5-86e3-b3929b4908fe" />
>
On a les 3 cités précedemment ainsi que k3d-lab-serverlb qui est un conteneur ayant pour image nginx qui va servir de load balancer
Un noeud est un conteneur qui fait tourner Kubernetes.
>

## Exercice 2 — Premier déploiement

3. Quels objets Kubernetes ont été créés par `kubectl create deployment` ? (indice : `kubectl get all`)
   >
   La commande a créé un ReplicaSet "web-68d995574f" et ce dernier a créé un pod "web-68d995574f-b8v9n"
   >
4. Vous avez supprimé le pod `web-...` : que s'est-il passé, et pourquoi ?
   >
   <img width="961" height="322" alt="image" src="https://github.com/user-attachments/assets/bc2745e7-091d-48ee-8fa7-b1c675b93420" />
   >
   Le pod supprimé est passé en "Terminating" et un nouveau pod a été crée automatiquement par ReplicaSet.
   C'est le système d'auto-réparation de Kubernetes
   >


## Exercice 3 — Modifier un conteneur en direct

5. Après suppression du pod, votre message « Bienvenue... » a-t-il survécu ? Pourquoi ?
   >
   Non il n'a pas survécu, car le pod a été récréé a partir de l'image nginx d'origine
6. Pourquoi le `port-forward` a-t-il cessé de fonctionner après la suppression du pod ?
   >
   Le port-fortward était connecté a l'ancien pod, lorsque ce dernier a été supprimé la connexion a aussi été perdu
   >

## Exercice 4 — Déclaratif

7. Quelle différence entre `kubectl create` et `kubectl apply` ?
   >
   kubectl create crée un objet une seule fois, et renvoie une erreur s'il existe déjà. kubectl apply applique l'état décrit dans le YAML : il crée l'objet s'il n'existe pas, ou le met à jour s'il existe
   >
8. À quoi sert le `selector` d'un Service ? Que se passe-t-il s'il ne correspond à aucun pod ?
   >
   Le selector indique au service quels pods vont recevoir le trafic, grâce à leurs labels (app=site dans notre exemple).        S'il ne correspond à aucun pod, le service n'a aucun endpoint et le site ne répond plus.
   >

## Exercice 5 — Scaling & mises à jour

9. Sur quels nœuds se trouvent vos 3 réplicas ? Collez la sortie de `kubectl get pods -l app=site -o wide`.
   ```

   ```
10. Avec l'image `nginx:9.99`, quel statut avait le pod ? Quelle commande vous a donné la cause ?
    >
11. Pendant la panne, le site restait-il accessible ? Pourquoi ?
    >

## Exercice 6 — Portainer & Mario

12. URL publique de votre Mario :
    >
13. Retrouvez le Deployment `mario` en ligne de commande. Portainer et `kubectl` parlent-ils au même composant ? Lequel ?
    >

## Bonus (facultatif)

14. Bonus réalisés et remarques :
    >

---

**Score obtenu avec `./scripts/check.sh` :** ... / ...
