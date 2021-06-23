---
layout: post
title:  "Présentation d'un jeu vidéo pour sensibiliser à l'écologie"
author: araynaud
categories: [ talk ]
image: assets/images/top2_gamejam/top2.png
published: false
---

Dans le cadre d’un challenge d’innovation, nous avons organisé un hackathon jeux-vidéos avec pour thème : empreinte. Le but du challenge étant de développer un jeu agréable, performant et divertissant en respectant au maximum le thème. 

Nous avons décidé de donner une dimension écologique au thème. Ainsi, notre jeu est un FPS dans lequel le joueur incarne un habitant qui doit tout faire pour diminuer l’impact carbone de sa ville. Le joueur a une jauge qui représente l’empreinte carbone de sa ville, et tout au long du jeu, cette jauge va augmenter ou diminuer en fonction d’évènements extérieurs ou d’actions du joueur. Ce dernier gagne lorsque la jauge est vide et perd dans le cas contraire. 

Afin de faire diminuer la jauge, le joueur effectue donc des actions écologiques : ramasser des choses par terre pour les jeter à la poubelle, éteindre les lampadaires qui ont une certaine consommation, etc. Des évènements aléatoires s’ajoutent aux actions du joueur pour faire évoluer cette jauge. Par exemple, si trop de lampadaires sont éteints pendant la nuit, a ville reçoit un malus qui va augmenter la jauge. 

Afin de rajouter un peu de défis, la carte est séparée en 2 par une route principale avec une circulation importante. Si une voiture touche le joueur alors il perd instantanément. 

Le jeu n’est pas gagnable en l’état. Comme vous le verrez par la suite, nous avons rencontrés différents problèmes qui ont fortement ralenti la progression du développement. Ainsi, plusieurs fonctionnalités permettant de faire diminuer l’impact carbone n’ont pas vu le jour. Voici une petite description de nos différentes idées.

Les améliorations qu’on aurait voulu apporter au jeu : 
- On avait pensé à rajouter un système d’argent gagné lorsque l’on ramène des déchets. Cela nous aurait permis de pouvoir acheter différentes choses dont des arbres et de les planter dans la map. Ce système d’arbre pourrait baisser régulièrement l’empreinte carbone du joueur. 
- Pour avoir un peu plus d’interactions dans le jeu, on aurait voulu générer des évènements avec les habitants. Par exemple on reçoit une notification disant que quelqu’un a déversé ses déchets sur la route. 
- La map est bien mais pas suffisamment grande pour nous... C’est pourquoi l’une de nos améliorations aurait porté sur la modification de la map. 
- Un système de popup d’aide à l’interaction a été imaginé mais par manque de temps, il n’a pas été mis en place. 

 

## Notre organisation 

### La map

Pour un objectif de rapidité et de simplicité nous avons décidé de prendre une map d’une ville en 3D déjà faite. Nous voulions absolument une ville très diversifiée, avec des maisons, immeubles, ruelles, lampadaires et des poubelles.  

Pour augmenter le réalisme, nous avions intégré de multitudes de poubelles (sac poubelle, benne à ordures, poubelle individuelle…) 

Un jour/nuit a été mis en place avec une lumière d’Unity qui procède à une rotation sur un axe.  

Lien map: https://assetstore.unity.com/packages/3d/environments/urban/city-package-107224 

Les interactions 

Afin d’améliorer l’expérience utilisateur, nous avons ajouté un trafic de voitures régulier, sur les 2 axes principaux de la ville. Si une voiture percute votre personnage, le jeu se termine. 

Lien voitures : https://assetstore.unity.com/packages/3d/vehicles/land/simple-cars-pack-97669 

Comme énoncé précédemment, l’objectif est d'interagir avec les éléments de la ville afin de diminuer l’impact carbone. Pour l’interaction vous avons utilisé RayCast sous Unity.  

Pour faire simple, on pourrait comparer le RayCast à un faisceau lumineux allant en ligne droite sur une distance donnée. 

Ce faisceau va nous permettre de vérifier s’il rentre en contact avec un autre objet, un tag ou des calques. Cela fait partie des fonctionnalités liées à la physique de Unity3d. 

Pour notre jeu, le RayCast permet d’interagir avec les lampadaires, attraper des objets et le jeter dans les poubelles.  


Les difficultés : 

Tous 3 intéressés par Unity nous avons décidé de faire cette jam avec cette technologie. Il s’agissait de premier jeu avec cette technologie ce qui a donné lieu à différents problèmes. 

Le fait de ne pas connaitre l’environnement nous a fortement ralenti dans le développement du jeu. La gestion de la formation et de la jam en simultané a été difficile. 

 

Etant débutant sur cette technologie, notre plus gros problème a été la gestion de git avec l’environnement Unity. En effet, chaque push donnait lieu à un merge sur des fichiers meta de Unity qui ont plusieurs fois bloqué nos environnements de travail 

On a également eu quelques problèmes avec les assets (lampadaires, poubelles, sacs ... ). En effet, on n’avait aucune connaissance sur comment modifier le comportement d’un objet. Faire clignoter les lampadaires de façon random a été plus difficile que prévu. 

 

Finalement, malgré le fait que notre jeu ne soit pas fini, la découverte de Unity dans un contexte de Jam était assez difficile mais intéressant. 

 

Comment build notre jeu : 

Il faut lancer la compilation avec la version 2019.4.16f1 de Unity. 

Une release est disponible sur github pour toutes les plateformes 

 

 

Images du jeu : 

 

