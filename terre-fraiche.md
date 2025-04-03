---
title: C'est en ligne
date: 2025-04-03
description: Le jardin est vivant
layout: note.njk
tags:
  - flux
---
Ce jardin prend doucement vie.
Pas encore de fleurs, ni d’abeilles. Juste la terre, fraîche et prête.
C’est le tout début.

J’écris mes notes dans Obsidian, sur mon téléphone, et elles se synchronisent automatiquement avec GitHub grâce à l’app Git Sync (mais il existe aussi un plugin Obsidian, je testerais plus tard).


Ces notes vivent dans un dépôt Git à part, que j’ai lié à mon projet 11ty comme un submodule Git.

À chaque push, une GitHub Action s’occupe de builder le site et de le déployer automatiquement sur jardin.ludique.dev.

Ça semble presque magique. Et pourtant, tout reste lisible, modulaire, ouvert.