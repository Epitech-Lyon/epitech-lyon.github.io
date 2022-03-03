---
layout: post
title:  "Delivr’aide"
author:
    - tom.debout@epitech.eu
    - daniel.tirrier@epitech.eu
    - matheo.robert@epitech.eu
categories: [ hubproject ]
image: assets/images/delivraid/poster.png
published: true
comments: false
featured: false
---  

Delivr’aide est un projet de l’association *l’Equipage Solidaire*[^eqp] ayant pour but d’aider les étudiants en situation de précarité, avec des kits alimentaires ou de première nécessité, en les livrant directement à domicile. 

> Delivr'aide est un projet de l'association *l’Equipage Solidaire*[^eqp] ayant pour but d’aider les étudiants en situation de précarité

## Comment avons-nous rejoint l’association ? 

Nous avons entendu parler pour la première fois de ce projet sur les réseaux sociaux, en effet une vidéo a été diffusée dans le but de faire connaître la plateforme et de trouver des bénévoles dans plusieurs villes: Paris, Montpellier, Lyon etc.. 

C’est à ce moment-là que nous avons contacté l’association pour devenir livreur bénévole sur Lyon. Nous envoyons donc notre candidature ! Nous recevons une réponse positive après quelques jours et nous sommes invités à une vidéo conférence pour nous expliquer le fonctionnement en détail de la plateforme et le déroulement des livraisons. 

Suite à notre entretien, nous avons vite reconnu qu’il y avait un certain manque d’organisation au sein de l’association.  
   
## La problématique

Les demandes étaient envoyées depuis un Google Form, récupérées par mail, transférées sur un excel, puis re-transférées sur un autre excel une fois qu’une livraison était programmée, puis envoyée sur un groupe WhatsApp dans lequel les livreurs s'inscrivaient pour effectuer la livraison.

Bref, en voyant ce processus énergivore et pouvant engendrer certaines erreurs humaines, nous nous sommes fixés pour objectif de mettre à disposition nos compétences pour essayer d’améliorer ce processus. 
   
## Notre solution

Nous prenons contact avec l’association pour leur proposer éventuellement de développer une application mobile ainsi qu’un nouveau site internet dans le but de consolider leur identité numérique ainsi que renforcer l’organisation des livraisons. 

Ils acceptent de nous faire confiance, et nous commençons alors notre veille technologique. 

**Les technologies retenues:** 
- *ReactJS*: Pour le site vitrine ainsi que l’interface administrateur, nous connaissions déjà cette librairie JavaScript et souhaitions l’intégrer au maximum dans le projet afin de développer nos connaissances. 
- *React-Native*: Ce framework permet de développer une version de l’application pour iOS et Android, ce qui représente un gain de temps considérable et se rapproche du fonctionnement de ReactJS. 
- *NodeJS/Express*: Pour le back-end nous avions commencé par Firebase pour la gestion de la base de données mais d’un point de vue technique, il était plus intéressant d’utiliser NodeJS avec Express pour mettre en place une API et y apprendre les notions associées.
- *MySQL (MariaDB)*: Pour la base de données nous avons utilisés MySQL que l’on ne présente plus, son utilisation à était couplé avec l’ORM Sequelize pour NodeJS côté API.

## Dans la peau de UX/UI Designers

Nous avons travaillé sur Figma pour les maquettes Web/Mobile bien que nous ne sommes pas du métier, nous avons essayé de nous débrouiller avec ces outils pour essayer de mettre en place une interface propre et compréhensible tout en respectant l’identité visuelle de Delivr’aide.

<table title="Aperçu du fichier Figma de l’application mobile">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-01.png" width="70%" height="auto"/></td>
</tr>
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-02.jpg" width="70%" height="auto"/></td>
</tr>
</table><font size=1pt color="sky-blue"> Fig. Aperçu du fichier Figma de l’application mobile </font>

<br> 

## De la maquette au prototype - Refonte du site vitrine

Nous avons refait le site internet de l'association afin de créer une identité visuelle commune aux différents outils que nous avons développés. Ce site permet d’introduire l’association avec différentes informations, le formulaire de demande de kits, différents formulaires pour venir en aide à l’association (devenir un livreur, devenir un partenaire ou encore un bénévole afin d’aider l’association à concevoir des kits), un lien vers la page de don “helloasso” et les différents contact nécessaire. 

Pour le site vitrine nous avons utilisé ReactJS et Firebase pour la gestion du formulaire de demande de kits. 

<table title="Aperçu du site vitrine">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-03.png" width="700" height="auto"/></td>
</tr>
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-04.png" width="700" height="auto"/></td>
</tr>
</table><font size=1pt color="sky-blue"> Fig. Aperçu du site vitrine </font>

<br> 

Une application mobile pour les livreurs et pour les étudiants, le but étant de réduire au maximum le nombre d'intermédiaires entre l’information. L’idée serait de déployer les livraisons disponibles directement sur l’application et de permettre aux étudiants de faire une demande / suivi de kit directement sur l’application. 

Dans un premier l’application fut commencée en Swift puis un revirement vers React-Native s’est imposé pour la facilité de portabilité entre Android et iOS. Nous avons développé une application mobile en React-Native qui se divise en 2 parties :

<img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-05.png" title="Page d’accueil" width="auto" height="auto"/>
<br> <font size=1pt color="sky-blue"> Fig. Page d’accueil </font>

- Une section pour les étudiants: Cette dernière contient un menu avec les différentes fonctionnalités misent en place/en cours de réflexion. 

<table title="Page d’accueil côté étudiant">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-06.jpg" width="200"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-07.jpg" width="200"/></td>
</tr>
</table><font color="sky-blue" size=1pt> Fig. Page d’accueil côté étudiant </font>

<br> 

<table title="Recevoir un kit">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-08.png" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-09.png" width="auto" height="500"/></td>
</tr>
</table><font size=1pt color="sky-blue"> Fig. Recevoir un kit </font>

<br> 

<table title="Suivre son kit">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-10.png" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-11.png" width="auto" height="500"/></td>
</tr>
</table>
<font size=1pt color="sky-blue"> Fig. Suivre son kit </font>
<br>
<table title="Vue des articles">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-12.png" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-13.png" width="auto" height="500"/></td>
</tr>
</table>
<font size=1pt color="sky-blue"> Fig. Vue des articles </font>
<br> 
 

- Une section dédiée aux livreurs : le livreur aura accès à une liste de livraisons, il pourra les accepter en fonction de son planning et pourra les annuler 24 heures avant s'il ne peut plus les assurer et aura une notification de l'équipe d'administration. 

<table title="Prévisualisation des différentes sections de l’interface livreur (1/2)">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-14.jpg" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-15.png" width="auto" height="500"/></td>
</tr>
</table><font size=1pt color="sky-blue"> Fig. Prévisualisation des différentes sections de l’interface livreur </font>
<br> 


<table title="Prévisualisation des différentes sections de l’interface livreur (2/2)">
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-16.png" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-17.png" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-18.png" width="auto" height="500"/></td>
</tr>
<tr>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-19.png" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-20.png" width="auto" height="500"/></td>
<td><img src="{{ site.baseurl }}/assets/images/delivraid/delivraid-15.png" width="auto" height="500"/></td>
</tr>
</table>
<br>

- une interface administrateur : toujours dans l’optique de garder les informations intactes durant le processus logistique, une interface administrateur s’impose pour gérer les comptes livreurs, gérer les livraisons publiées etc. Sur la même base que le site vitrine nous avons utilisé ReactJS ,Firebase, NodeJS, l’aspect front-end a été couplé avec Bootstrap afin d'accélérer le développement de cette dernière. 

<img title="Page d'accueil de l’interface administrateur" src="{{ site.baseurl }}/assets/images/delivraid/delivraid-21.png"/>
<br> <font size=1pt color="sky-blue"> Fig. Page d'accueil de l’interface administrateur </font>

<img title="Page d’ajout de livraison de l’interface administrateur" src="{{ site.baseurl }}/assets/images/delivraid/delivraid-22.png"/>
<br> <font size=1pt color="sky-blue"> Fig. Page d’ajout de livraison de l’interface administrateur </font> 

## Organisation et persévérance au cœur du projet

La plupart des technologies abordées étaient nouvelles pour nous, la documentation et réflexion étaient les freins de ce projet. 

Nous avons appris le fonctionnement de la plupart des technologies ainsi que leurs utilisations en les pratiquant au fur et à mesure, à chaque blocage nous avons pu compter sur la bienveillance de la communauté de développeurs sur différents forum, nous permettant ainsi de comprendre nos erreurs et le fonctionnement des processus auxquels nous faisions usage. 

Notre but étant de proposer un écosystème synchronisé et fonctionnel avec un code propre, peu gourmand, disponible sur toutes les plateformes, à notre échelle, le défi est de taille! Pour parvenir à ce but, le plus important a été de comprendre correctement les notions que nous abordions pour pouvoir atteindre notre objectif, et ne pas foncer tête baissée dans le fonctionnel. Certaines fonctionnalités peuvent apparaître au fil du temps, d'autres disparaissent, l’application s’améliore de jour en jour, ce qui demande une activité très régulière. Le projet est de taille mais nous sommes motivés à aller jusqu’au bout, nous sommes heureux de participer à une cause qui sera bénéfique à nos confrères et pourquoi pas plus dans le futur.  L’association est en pleine expansion et nous comptons bien frapper un gros coup pour développer cette initiative ! 

## Références   

[^eqp]: [L'Equipage solidaire](https://equipagesolidaire.org/)