---
layout: post
title:  "Click & Collect"
author: jhouvenaghel
categories: [ hubproject ]
image: assets/images/clickncollect/logo512.png
---
Quel outil pour fluidifier la prise de commande pendant les horaires de pointe? Voilà le besoin technologique auquel j'ai essayé de répondre à travers ce projet hub.

L'idée m'est venue en voyant la queue qu'il pouvait y avoir devant le BDE, comme des horaires de pointes.
Par exemple, les pauses en piscine. J'ai alors pensé à faire comme les restaurants de fast-food, où l'on pouvait commander en amont et récupérer sa commande à une heure précise pour éviter le temps d'attente, d'où le nom: Click N Collect.

J'ai également pensé à ajouter une gestion basique de stock (disponible/indisponible) pour éviter les mauvaises surprises.

## Réalisation

Click N Collect a pris forme sous un bot messenger (facebook), messenger étant la plateforme la plus utilisée pour communiquer entre les étudiants Epitech. Cela évitait la création d'un compte quelque part, ou alors de mémoriser une énième plateforme. C'était aussi une découverte pour moi, ayant toujours voulu tester la programmation de bots.

Le projet s'articule de la manière suivante:

- Encapsulation complète sur Docker
- Base de donnée en SQLite
- Back en Python
- Front en React

Le front correspondait ici au panel d'administration permettant de gérer les stocks pour les membres du BDE.