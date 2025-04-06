---
title: C'est en ligne
date: 2025-04-03
description: Le jardin est vivant
layout: note.njk
tags:
  - tech
---
Ce jardin numérique prend doucement vie. Les fondations techniques sont en place, prêtes à accueillir les premières pousses.

La stack technique est posée :
Un générateur de site statique (SSG) avec 11ty (eleventy), choisi pour sa simplicité et ses performances. Le contenu est rédigé en Markdown.

Pour l'édition, n'importe quel éditeur Markdown ferait l'affaire. Personnellement, j'ai opté pour Obsidian (avec applications mobile et desktop). C'est un éditeur très flexible et populaire, qui interprète nativement le frontmatter utilisé par 11ty. Cela me permet d'écrire et d'ajouter des métadonnées facilement depuis un ordinateur ou un téléphone.

Un autre avantage est que mes notes sont également accessibles hors ligne, stockées localement sur mes appareils, et la synchronisation se fait via GitHub. Les notes ont leur propre dépôt Git, séparé du code du site. Pour les rendre accessibles à 11ty au moment du build, une GitHub Action commence par cloner ce dépôt de notes directement dans le répertoire source du projet 11ty.

De cette façon, je peux séparer le contenu (les notes) du contenant (le code du site). Dans mon cas, cette méthode s'est avérée plus efficace à gérer au niveau de l'intégration continue (CI/CD) que l'utilisation de Git submodules, qui posait des soucis de versions de modules pas à jour avec l'état du contenu.

Ainsi, à chaque push de nouvelles notes ou sur le dépôt Git du contenu, une GitHub Action se déclenche pour notifier le dépôt SSG. Ce dernier clone le contenu et construit l'intégralité du site avec 11ty, puis le déploie sur une GitHub Page accessible via l'adresse jardin.ludique.dev.

Le processus, une fois en place, semble presque magique !