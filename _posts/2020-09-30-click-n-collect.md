---
layout: post
title:  "Click N Collect"
author: jhouvenaghel
categories: [ hubproject ]
image: assets/images/clickncollect/logo192.png
---
Quel outil pour fluidifier la prise de commande pendant les horaires de pointe? Voilà le besoin technologique auquel j'ai essayé de répondre à travers ce projet hub. L'idée m'est venue en voyant la queue qu'il pouvait y avoir devant la boutique du **BDE** (Bureau des étudiants) de mon école pendant les horaires de pointe. J'ai alors pensé à faire comme les restaurants de fast-food, où l'on pouvait commander en amont et récupérer sa commande à une heure précise pour éviter le temps d'attente, d'où le nom: **Click N Collect**.

Je voulais une solution très simple d'accès d'où l'idée d'utiliser les services chatbot de [Facebook][3]. Le chatbot permet aux étudiants de passer des commandes - il communique avec un serveur pour la gestion des stocks (pour éviter les mauvaises surprises).

## Réalisation

Click N Collect a donc pris la forme d'un [bot messenger][3] - la plateforme la plus utilisée pour communiquer entre les étudiants Epitech. Cela évite la création d'un compte quelque part, ou encore, de mémoriser une énième plateforme. C'était aussi une découverte pour moi, ayant toujours voulu tester la programmation de bots.

Ci dessous, les technologies utilisées pour programmer la solution :

- Livraison : [Docker][2] + [Git][1]
- Gestion des données : [SQLite][5]
- Back : [Python-Flask][4]
- Front (panel admin pour la gestion des stocks pour les membres du BDE) : [ReactJs][6]

La solution complète est *forkable* depuis la [page github d'Epitech-Lyon][1]

[1]: http://github.com/epitech-lyon/ClickNCollect
[2]: https://www.docker.com/
[3]: https://developers.facebook.com/products/messenger/
[4]: https://flask.palletsprojects.com/en/1.1.x/
[5]: https://sqlite.org/index.html
[6]: https://reactjs.org/