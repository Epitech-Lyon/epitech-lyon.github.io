---
layout: post
title:  "Vhex (Kernel pour les calculatrices Casio)"
author: ymagnin
categories: [ hubproject ]
image: assets/images/vhex/vhex.jpg
published: true
---

L'année dernière, j'ai choisi de faire comme [projet Hub][4] un kernel pour les calculatrices Casio. Comme le projet est toujours d'actualité et que j'ai l'opportunité de partager mes prévisions pour la suite, je vais essayer d'expliquer le plus possible l'objectif derrière ce noyau.

---

### Motivations

Avant de commencer, je vais tenter de répondre à une question qu'on m'a posée pas mal de fois, à savoir : "pourquoi choisir une calculatrice ?". Le fait de bosser sur une machine dont la specification est très limitée est intéressant : ça apprend des techniques de rétro-ingénieurie, ça permet d'être dans un état "d'exploration", intrigué par tout ce qu'on trouve et toujours prêt à découvrir une nouvelle horreur de Casio, ou un petit truc sympatique que personne n'avait exploité avant.

Bien entendu, en terme d'efficacité, et surtout de liberté, je donnerais beaucoup pour travailler avec un matériel connu, libre, et bien documenté. Mais pour le moment, il n'y a pas de tel matériel, donc je m'amuse avec ce que j'ai sous la main et que je connais assez bien désormais. Arrêter de coder pour le fun, ce serait pousser l'esprit du libre tellement loin qu'il deviendrait paradoxal : la première forme de liberté, c'est de faire ce qui nous fait plaisir, non?

Par contre, je préfère mettre les choses au clair dès le début, le projet n'a pas pour but d'être un kernel révolutionnaire, si vous avez envie de faire un OS meilleur que celui de Casio pour lancer des super-jeux en 3D, connecter votre calculatrice à Internet, ou encore avoir une interface plus jolie que ce bon vieux menu de nos Casio, ce n'est __PAS__ mon but. Un projet comme Vhex m'oblige à apprendre, comprendre, mettre en pratique des dizaines de thèmes différents, tout en me donnant de plus en plus la capacité de visualiser clairement les problèmes rencontrés dans la programmation de noyaux.

---

### Explication du projet

Pour en revenir au sujet, mon envie première est de mettre en place plusieurs projets qui sont plus ou moins "liés" entre eux et qui ont pour objectif principal de fournir un kernel UNIX-like libre pour les calculatrices Casio (mais je pense qu'avec une bonne organisation, il ne devrait pas y avoir trop de difficulté à porter le projet sur une architecture différente).

Vous avez ici la vue d'ensemble des projets :

```
------------------------------------------------------------
| Kernel / OS             | Librairies                     |
|-------------------------|--------------------------------|
| fxBoot (bootloader)     | fxlibc (C standard librairies) |
|   |-- FixOS (OS)        | fxCompositor (windows manager) |
|   `-- Vhex (kernel)     | fxGUI (graphical librairies)   |
|        |-- GladOS (OS)  |                                |
|        `-- testOS (OS)  |                                |
------------------------------------------------------------
```

Chaque partie que vous voyez la sera indépendantes pour permettre à quiconque le souhaite de participer au projet.

---

### Petite description des projets :
<ins>FxBoot: (bootloader)</ins><br>
C'est un bootloader qui permettra de charger les noyaux sur la machine (mais aussi les addins). C'est une des parties les plus importantes du projet et j'aimerais qu'il ait suffisamment de souplesse pour arriver à charger des OS qui n'ont pas été pensé pour être loader (par exemple FixOS).

<ins>FixOS: (OS)</ins><br>
Un OS pour les vieilles calculatrices SH3 développé par Kristaba il y a quelques années maintenant. Il ne fait pas partie du projet mais c'est juste pour indiquer que Vhex ne sera probablement pas porté sur SH3 pour des raisons techniques (et matériel car je n'ai pas de SH3 fonctionnel sous le coude).

<ins>Vhex: (kernel)</ins><br>
La pièce maitresse du projet. C'est mon kernel que j'ai développé l'année précédente et qui étais presque arrivé au stade de FixOS. Cependant, l'architecture ne me plait pas (monolithique non-modulaire) et j'aimerais que chaque fonctionnalité du noyau puisse être chargé sur demande (via des modules kernel, qui seront probablement des librairies dynamique). Un topic sera créé pour vous tenir au courant des dernières avancées et pour vous permettre de me proposer des correctifs ou des features que vous aimeriez bien voir sur le noyau (je ne vous promets pas de les réaliser ceci-dit )

<ins>GladOS: (OS s'appuyant sur Vhex)</ins><br>
C'est mon premier prototype de kernel que j'avais commencé à réaliser il y a plus d'1 an maintenant. Il a toujours pour objectif de remplacer Casio de la machine mais il se basera sur Vhex pour fonctionner (et non un truc custom). Il permettra d'utiliser la machine à son plein potentiel (driver USB, gestion de la mémoire virtuelle, EEPROM, ...).

<ins>TestOS: (OS s'appuyant sur Vhex)</ins><br>
C'est un "OS" qui, actuellement, se base sur un fork de Vhex et qui me permet de tracer l'OS de Casio pas-à-pas, faire des tests hardware, analyser la RAM. C'est un truc absolument pas stable mais très utile pour faire de la rétro-ingénierie directement sur la calculatrice. Il se basera entièrement sur Vhex à l'avenir. Par contre, je ne pense pas donner les sources avant de l'avoir sécurisé un minimum (car le code manipule beaucoup de choses dangereuses pouvant casser la calculatrice si on ne sait pas ce qu'on fait. (si vraiment vous les voulez, je peux vous les donner hein? Faites juste gaffe avec)).

<ins>fxlibc: (librairie standard C pour les calculatrices Casio)</ins><br>
C'est un projet que j'ai commencé récemment et qui a pour but de fournir une libraire standard pour les calculatrices et qui pourra être configurable (par exemple pour permettre de choisir l'ABI que l'on souhaite (Casio, Vhex ou FixOS), le format, ...). Elle sera utilisée pour la plupart des projets liés au noyau.

<ins>fxGui: (libraire graphique)</ins><br>
Ce sera une librairie qui fournira un moyen pour les gestionnaires de fenêtres "composite" de communiquer directement avec les applications graphiques ainsi que le matériel vidéo.

<ins>fxCompositor: (compositing window manager)</ins><br>
Ce sera un gestionnaire de fenêtres de Vhex (un logiciel chargé de l'affichage et du placement des fenêtres d'applications) qui reprendra le fonctionnement de Wayland.

---

### Où est-ce que ça en est aujourd'hui ?

Je suis encore en train de mettre sur papier la nouvelle architecture du noyau histoire de voir toutes les possibilités qui pourraient être implémentées. Mais je suis confronté à plusieurs problèmes techniques assez complexes à résoudre proprement, notamment concernant le chargement des modules kernel (sans rentrer dans les détailles, la `toolchain` utilisée ne permet pas de générer des librairies dynamiques qui sont essentielles pour charger des bouts de code "à-la volée") ce qui est fort cocasse étant donnée que la nouvelle architecture du noyau repose dessus .

Aussi, je suis en train de documenter la machine le plus possible avant de me replonger dans le développement des projets.
J'ai plusieurs cibles notamment :
* Fugue, le "nouveau" système de ficher propriétaire utiliser par les "nouvelles générations" de calculatrice Casio.
* Le driver USB de Casio. Grâce à Lephenixnoir (un illustre ami et administrateur de Planète Casio), on a pu certifier que le module hardware qui gère l'USB et pratiquement le même que sur le processeur `SH7724` mais je n'arrive toujours pas avoir les infos sur le bus ainsi que de notifier l'hôte que je suis connecté.
* l'ABI de la Graph90+E, qui n'est pas aussi biens connu que sur monochrome.

À part ça, j'ai commencé à créer la [fxlibc][5], la librairie C standard que j'utiliserai pour mes projets. Je sais que Memallox a porté `newlib` sur la calculatrice mais j'ai besoin d'avoir quelque chose de suffisamment modulaire pour choisir quel ABI je veux utiliser (CASIOABS, Vhex ou FixOS) ainsi que le format de la librairie (statique '.a' ou dynamique '.so'). J'ai encore quelques hésitations sur le comment architecturer tout ça mais je ferrai un topic quand j'aurais à nouveau du temps devant moi. Dites-vous que le prototype est quasiment finis, il manque juste énormément de fonction (que j'ajouterai au fur et à mesure de mes besoins) ainsi que de l'optimisation sur toutes les fonctions.

J'ai aussi commencé à poser sur papier les features du bootloader ainsi que sa documentation. Une fois le prototype de la `fxlibc` finie ce sera ma priorité. Là aussi je ferrais un topic quand j'aurais commencé a dev quelque chose. Tous ce que je peux dire pour l'instant c'est qu'il reposera uniquement sur les fonctionnalités de l'OS de Casio pour faciliter son portage.

Je sais d'avance que cette année ainsi que l'année qui arrive risque d'être compliqué pour continuer ces projets. C'est pourquoi, si vous avez envie de participer, vous êtes les bienvenus !

---

### Prévisions avant juin 2021
J'aimerais avoir :
* un prototype correct du bootloader pouvant tourner sur toutes les calculatrices Casio qui supporte les addins.
* la libc supportant l'ABI de Vhex ainsi que la création de librairies dynamique.
* une documentation / organisation correcte pour que n'importe qui puisse continuer.
* un "prof-of-concept" de Vhex en version modulaire.

J'espère sincèrement que le projet prendra vie et arrivera à maturité. Dans tous les cas, de tous les projets annoncés, j'ai déjà réalisé des "proofs of concept" qui trainent de mon côté, je peux donc vous affirmer que le projet serait réalisable ! Le challenge va être d'organiser et maintenir tout ça dans le temps.

---

### Annexes
* [Le topic principal peut-être trouve sur Panet-Casio][1]
* [Les sources de mon kernel se trouvent sur le Gitea de Planet-Casio également][2]
* [Mes notes sur la rétro-ingénierie du processeur SH7305][3]


[1]: https://www.planet-casio.com/Fr/forums/topic16469-1-projet-vhex-kernel-pour-les-calculatrices-casio.html
[2]: https://gitea.planet-casio.com/Yatis/Vhex-kernel
[3]: https://bible.planet-casio.com/yatis
[4]: https://github.com/Epitech-Lyon/Vhex-kernel
[5]: https://github.com/Epitech-Lyon/fxlibc