---
title: C'est en ligne
date: 2025-04-03
description: Le jardin est vivant
layout: note.njk
tags:
  - tech
---
Ce jardin numérique prend doucement vie
Les fondations techniques sont posées, et il est prêt à accueillir ses premières pousses.

La base technique (la “stack”): 
J’ai choisi un générateur de site statique appelé 11ty (ou Eleventy). Il est léger, rapide et simple à utiliser.
Les contenus sont rédigés en Markdown, un format de texte très lisible et facile à apprendre.

Une rédaction simplifié :
Pour rédiger, j’utilise Obsidian, un éditeur de notes avec app mobile desktop. Il est populaire, personnalisable, et surtout :
– Il comprend le frontmatter (des métadonnées en haut des fichiers) utilisé par 11ty,
– Il permet de travailler hors ligne, avec les fichiers stockés localement sur mes appareils.

J’ai organisé mon projet en deux parties :
Un dépôt Git pour le contenu (les notes),
Un autre dépôt pour le site web (le code 11ty).
Cela me permet de maintenir une séparation entre contenu et contenant.
Chaque fois que je modifie mes notes, une GitHub Action s’enclenche :
Elle clone le dépôt de notes,
Intègre ces fichiers dans le projet 11ty,
Génère le site à jour,
Et le publie automatiquement sur jardin.ludique.dev.

J’avais testé les Git submodules, mais j'ai rapidement rencontré des soucis de synchronisation.
Avec cette nouvelle méthode, c'est plus fluide.
Je pousse mes notes → GitHub fait le reste.

---

Résultat ?
Un processus automatisé, fiable, élégant.
Presque magique.

---

`+-------------------------+
| 1. Édition des notes    |
|    (Obsidian, local)    |
+-----------+-------------+
            |
            | git push
            v
+-----------+-------------+
| 2. Dépôt GIT 'Contenu'  | ----+
|    (GitHub)             |     | 3. Push -> Déclenche notif.
+-------------------------+     |
                                v
+-------------------------+ <---+
| 4. Dépôt GIT 'SSG'      |
|    (Code 11ty, GitHub)  | ----+
|    (Reçoit notif.)      |     | 5. Notif. -> Déclenche Action
+-------------------------+     v
                      +---------+---------------+
                      | 6. GitHub Action (SSG)  |
                      |-------------------------|
                      |  a. Clone Dépôt Contenu |
                      |  b. Build (11ty)        |
                      |  c. Deploy site         |
                      +---------+---------------+
                                | 7. Déploiement vers...
                                v
                      +---------+---------------+
                      | 8. GitHub Pages         |
                      | (jardin.ludique.dev)    |
                      +---------+---------------+
                                | 9. Site accessible par...
                                v
                      +---------+---------------+
                      | Visiteur                |
                      +-------------------------+

*Note: La notification est souvent gérée par une petite action sur le dépôt 'Contenu' qui en déclenche une plus grosse sur le dépôt 'SSG'.
`