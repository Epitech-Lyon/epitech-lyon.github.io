---
layout: post
title:  "Unreal Engine Workshop (1)"
author: meynard-longuet
categories: [ workshop ]
image: assets/images/unreal/affiche.jpg
published: true
---

Bonjour et bienvenue à tous sur ce Post-Workshop. L'on m'a demandé de vous retranscrire ce Workshop pour pouvoir le reproduire de votre côté. Il évoluera certainement au fur et à mesure de vos retours si des choses sont à corriger par la suite. 

Ni une, ni deux, rentrons dans le vif du sujet !


## Prérequis
- Installer Unreal Engine 4.20 (ou une autre version ultérieure)
- Une souris, c'est plus simple pour naviguer en 3D, la manette fonctionne aussi
- Clavier en QWERTY (Juste passer la langue en ENG suffit pour travailler simplement, ou alors, amusez-vous à modifier les options de l’éditeur ou encore importez un preset Français)


## Résumé de l'Unreal Engine Workshop - Partie 1
En premier, nous allons découvrir l'**Epic Games Launcher**, le cœur d'**Unreal Engine**. Si vous avez l'habitude de l'utiliser pour Fortnite, tant mieux, mais peu de gens regarde la partie **Unreal Engine**. 
Nous allons donc y jeter un œil.

Ensuite, nous regarderons l'**Éditeur**, sa façon de fonctionner, ainsi que l'agencement de ses fonctionnalités.
Vous apprendrez à le modifier à votre convenance, l'utiliser, et à vous poser les bonnes questions.

Vous découvrirez aussi que l'**Unreal Engine** n'est pas seulement un moteur de jeu, mais bien une suite pouvant s'adapter à vos besoins : cinéma, architecture, robotique, intelligence artificielle, réalité augmentée et virtuelle…

Par la suite, nous passerons à notre premier projet en commençant par les bases de l'**Éditeur** en créant notre première maison. D'une pièce au départ, elle s'agrandira par la suite selon votre envie.
Pour cela, nous apprendrons à utiliser les **Materials**, simplement, en les appliquant sur des **Meshes**.
Nous apprendrons aussi à mettre de la lumière dans nos **Scenes** et nous créerons un **Landscape** pour y poser notre maison.

Après avoir pris en main l'**Éditeur**, nous allons débuter la programmation. Ici, pas de **C++** pour que le cours soit accessible à tous, mais de la programmation visuelle : des **Blueprints**.
Premièrement, nous réaliserons une porte automatique s'ouvrant en passant devant. Pour cela, nous apprendrons à importer les **Assets** fourni par Epic Games, ceux du **Launcher**, mais aussi les votre !

Nous parlerons aussi de **Git**, et de comment l'utiliser pour l'**Unreal Engine** !

Pour terminer, je vous laisserai découvrir les **Blueprints** plus en profondeur avec quelques pistes !

## Epic Games Launcher
### **Onglet Unreal Engine (Anciennement Communauté)**
Une fois téléchargé, et installé, vous devriez arriver sur une fenêtre similaire, si non, cliquez sur Unreal Engine dans le choix de la catégorie :
<div align="center">
<a id="EGL_1"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/EGL_1.jpg?raw=true" width="700" height="" /></a>
</div>

<br>

Pour le moment, rien de bien compliqué sur cette page ! Vous pouvez y retrouver les news importante en premier plan, les liens de news, channel YouTube d'Unreal, le StackOverflow d'Epic, le Forum et la Roadmap (pas la peine de développer une feature si une qui arrive vous convient ! :smirk:)

En dessous, vous pourrez retrouver les informations récentes, et sur la droite, les projets de la communauté ! D'où son ancien nom : Communauté.

### **Onglet Apprendre**
Le second onglet, l'onglet Apprendre, regroupe pas mal de choses !
<div align="center">
<a id="EGL_2"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/EGL_2.jpg?raw=true" width="700" height="" /></a>
</div>

<br>

- <a  href="https://docs.unrealengine.com/en-US/index.html">**Documentation**</a> : Comme son nom l'indique, vous trouverez toute la Documentation de l'Éditeur. Allant simplement de la création de votre premier projet, au scripting de l'éditeur, en passant par la création de test unitaire ou la modification du moteur ! Vous pourrez tout trouver ici.<br/>

- <a  href="https://learn.unrealengine.com/home/dashboard">**Unreal Online Learning**</a> : Anciennement Unreal Academy, ce sont des **MOOC**. Des cours en ligne vidéo quoi, tout simplement. Très utile pour maîtriser certaines fonction de l'éditeur, ou juste pour apprendre. Pas mal de contenu spécialisés (**Quixel**, **Procedural**, **Blueprints**…)<br/>

- <a  href="https://forums.unrealengine.com/unreal-engine/announcements-and-releases/1745504-a-new-community-hosted-unreal-engine-wiki">**Community Wiki**</a> : Devenu poussière, il est peut être en train de renaître de ses cendres grâce à quelques efforts de la communauté.<br/>

- Le reste sont des **Quick Start Guide**, ainsi que des projets template pour se familiariser avec des features ou notions.<br/>

### Onglet Marché
Le troisième onglet, sûrement celui qui fera couler le plus d'encre, j'ai nommé : Le Marché !
<div align="center">
<a id="EGL_3"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/EGL_3.jpg?raw=true" width="700" height="" /></a>
</div>

<br>

Le marché est un onglet très intéressant si vous n'êtes pas un artiste dans l'âme. D'ailleurs si vous en êtes un aussi. Vous pouvez trouver énormément d'Assets gratuitement, d'autant plus qu'Epic Games en fourni chaque mois. De plus, rien ne vous empêche de modifier les assets achetés pour les adapter à votre jeu.

Un article était sortie sur le sujet il y a pas mal de temps, si vous souhaitez le retrouver, la partie se nomme **Modify and make assets your own**.

### Onglet Bibliothèque
On arrive enfin aux choses sérieuses, ce qui nous va nous intéresser le plus dans le launcher : la bibliothèque.
<div align="center">
<a id="EGL_4"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/EGL_4.jpg?raw=true" width="700" height="" /></a>
</div>

<br>

Je crois qu'ici, tout est explicite, sauf peut-être le **Coffre**. C'est ici que vous pourrez télécharger, ajouter au projet, et parfois créer des projets à partir de ce que vous avez acheté. Vous y retrouverez donc vos plugins, assets et autres démos.

C'est avec cela que nous terminons sur l'Epic Games Launcher. Nous rentrons désormais au coeur de ce Workshop : l'Unreal Engine.

## Unreal Engine 4
### Launcher
Une fois l'Unreal Engine 4 lancé, vous  devriez arriver sur un écran similaire.
<div align="center">
<a id="UEL_1"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/UEL_1.jpg?raw=true" width="700" height="" /></a>
</div>

<br>

Créons donc notre premier projet.

Pour cela : Games > Blank > Blueprint ou **C++ si vous comptez en faire, mais notre introduction n'en comportera pas** et gardez bien le Starter Content, sinon vous devrez l'ajouter par la suite. Nommez votre projet, puis **Create Project**.

### Editeur
Après création de votre projet, si vous n'arrivez pas sur une scène similaire à celle-ci. C'est soit que vous avez oublié le Starter Content, soit que votre Projet n'est pas un Jeu.

<div align="center">
<a id="UE_1"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/UE_1.jpg/?raw=true" width="700" height="" /></a>
</div>

<br>

> 🔍 DÉCOUVERTE
>
> Prenez le temps d'explorer l'éditeur, sa gestion des fenêtres, et ses différents menus.
>
> N'hésitez pas à aller voir **Editor Preferences** et **Project Settings** (dans Edit), ils sont très importants !
>

### Votre premier niveau
Désormais, à vous de jouer ! File, New Level… et Default (ou Time Of Day si vous ne souhaitez pas trop vous occuper des lumières).
Le but est d'arriver à un résultat similaire aux images ci-dessous.

<div align="center">
<a id="UE_2"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/UE_2.jpg?raw=true" width="700" height="" /></a>
</div>

<br>

> 💭 RÉFLEXION
>
> A vous d’essayer ! Essayez de faire quelque chose de similaire (intérieur, extérieur ou même les deux) ! 
>
> Jouez avec les effets, formes et Materials. Soyez créatifs !
>

> 🎯 ASTUCE
>
> N'hésitez pas à utiliser les Box de Geometry en Additive ou Substractive. Voir même l'outil **Geometry Editing**.
>

> 🔍 DÉCOUVERTE
>
> Prenez votre temps et n'hésitez pas à travailler à plusieurs ou demander de l'aide. Vous pouvez même aller voir le <a href="https://docs.unrealengine.com/en-US/Engine/QuickStart/index.html">Quick Start Level Design en cliquant ici</a>.
>

### Blueprints
Les **Blueprints** sont un système de **programmation visuel** développé pour Unreal Engine permettant de scripter son jeu sans savoir programmer.

Cependant, il est aussi complémentaire avec le C++, utiliser les deux permet de gagner du temps tout en ayant une optimisation finale quasi-identique.
Il ne faut pas voir l'un comme le remplaçant de l'autre, mais coinjointement. Même si les Blueprints tendent petit à petit à s'imposer face au C++ d'Unreal au vu de sa facilité...

Voici à quoi cela ressemble !
<div align="center">
<a id="UE_3"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/UE_3.jpg?raw=true" width="700" height="" /></a>
</div>

<br>

### Votre premier Blueprint
C'est maintenant que cela va devenir intéressant ! Nous allons créer le dernier sort des RPG à la mode ! Non en fait, nous allons simplement faire... Une porte automatique, activé par une **plaque de pression**.

Rien de bien compliqué pour commencer, c'est promis. (Et vous pourrez même en faire un labyrinthe de porte) Juste de quoi se mettre en pleine immersion... ! 🙃

Pour créer votre premier Blueprint, utilisez **Add New** dans le **Content Browser**, et choisissez **Blueprint Class*. Nous allons créer un **Actor**. Un Actor est tout simplement, comme l'éditeur vous l'indique, un objet  pouvant être placé ou pouvant apparaître dans le monde (**Level**). Appelez-moi ça BP_Door. Pourquoi **BP_** ? C'est simple : Un préfixe signalant que l'asset est un Blueprint. Cela est loin d'être obligatoire, mais je trouve cela plus simple à comprendre. L'<a href="https://github.com/Allar/ue4-style-guide">UE4 Style Guide</a> de Allar le propose aussi. L'Asset Naming Convention d'Unreal le proposait aussi, cependant elle n'est plus disponible à la suite de la première fermeture du Wiki... A vous de chercher, des bouts sont disponibles sur Internet, du genre <a href="https://www.gamecoderblog.com/en/unreal-engine4/ue4-recommended-files-naming-convention">ici</a> !

Bon, revenons à nos Blueprints. Ouvrez votre BP_Door. Cette fenêtre que vous venez d'ouvrir est comme un onglet, vous pouvez la mettre dans la liste d'onglet de l'éditeur.

La fenêtre Blueprint se compose de plusieurs parties, contenant elle aussi des onglets :
- **Viewport** : C'est ici que vous gérerez la partie 3D du Blueprint, ajoutant des composants Static Mesh(SM_/S_) ou d'autres choses que vous pourrez découvrir plus tard.
- **Construction Script** : Ce script s’exécutera à chaque instanciation du Blueprint, c’est un
peu grâce à cela que vous pourriez construire un asset procédural.
- **Event Graph** : C’est ici que vous pourrez programmer toute la logique de l’objet, nous
allons y venir pour ouvrir notre porte !
- **Details** : Correspond aux options de l’objet (ou variable) sélectionné.
- **My Blueprint** : Contient les différentes variables, fonctions et macros de votre Blueprint.

Bon, assez parlé, on fait cette porte ? Oui, on y vient. Pour créer cette porte, il nous faut ajouter un **Static Mesh** au **Viewport**, n'est-ce-pas ? Pour cela, allez dans l'onglet Viewport et **Add Component** > **Static Mesh**. Nommez le Door, ou quelque chose du genre... **SM_Door** par hasard 😉 ?

Maintenant, sélectionnez votre Components SM_Door, et utilisez le menu déroulant dans la partie Static Mesh où vous pourrez lui assigner une porte du Starter Content !

Vous n'avez pas ajoutez le Starter Content comme prévu ? Pas bien ! Mais pas bien grave, pour l'ajouter, faites comme lorsque vous avez voulu créer votre Blueprint : **Add New** > **Add Feature or Content Pack** (tout en haut) > **Content Packs** > **Starter Content**.

Tadah ! Vous pouvez sauvegarder, votre premier Blueprint fonctionne ! C'est super cool non ? Enfin... Ce n'est pas comme si il faisait quelque chose pour le moment... !

Je vous laisse vous amuser avec l'éditeur, et plus précisement ce qui se trouve dans votre Blueprint, une fois ceci fait, vous pourrez passer à la partie suivante !

> 🔍 DÉCOUVERTE
>
> Prenez votre temps et n'hésitez pas à travailler à plusieurs ou demander de l'aide.
>
> Si vous n'êtes pas à l'aise, cela pourrait s'avérer compliqué par la suite ! Alors, prenez votre temps.
>
> A vous de jouer !
>

### Votre premier script Blueprint
Enfin un peu de programmation !

Allez dans l'**Event Graph** de votre Blueprint et... Supprimez tout. Tout ce que vous voyez dans l'Event Graph, **pas ailleurs**. Cependant, n'hésitez pas à jeter un coup d'oeil avant, c'est préférable ! Fait ? On peut désormais passer au coeur du sujet.

Créez une nouvelle **variable** et appelez là **Trigger**. Modifiez son **Type** pour **Trigger Volume > Object Reference**. Normalement Object Reference est l'option de base, mais ne sait-on jamais. Activez l'option **Instance Editable** dans la variable et appuyez sur Compile !

**L'option Instance Editable peut se soit modifier dans les détails de la variable, soit en cliquant sur l'oeil au niveau du nom de la variable. A vous de choisir !**

Retournez sur votre niveau, et glissez votre BP_Door à l'intérieur. Sélectionnez-le et... Vous avez accès à la variable Trigger que vous pouvez directement définir une fois que vous aurez un **Trigger Volume** dans votre niveau. Cela permet d'éviter de la définir en dur, et nous fait profiter au maximum de la capacité des Blueprints, surtout en tant que débutant.

> 🎯 ASTUCE
>
> Vous pouvez faire glisser les variables directement dans l’Event Graph ! Essayez pour voir, créez-en même de nouvelles, découvrez les différents types…
>
> Imaginez ce que cela pourrait être ou faire ! Pour ajouter des nœuds : clic droit !
>

Bon, c’est bien joli tout ça, mais il faut qu’on fasse quelque chose pour que la porte s’ouvre quand nous entrons dans le Volume non ? 
Sélectionnez la variable Trigger et dans Events, appuyez sur le [+] de **On Actor Begin Overlap**, faites la même chose pour **On Actor End Overlap**. 
Pour celles et ceux qui auraient du mal, cela signifie que : Quand un acteur entre dans la zone de l’objet, ou la quitte.

Vous avez compris ce que vous devez faire dans l’Event Graph maintenant ? Non ? Pas encore ? Allez, je vous aide !
- Get SM_Door node (Le Drag&Drop des Components fonctionne... Ou la barre de recherche clic droit aussi)
- LocalRotation node (Set ou Add ? X, Y ou Z ? En fonction de quel objet ?)

N’oubliez pas d'utiliser votre Trigger Volume dans l’éditeur aussi... 😉

> 💭 RÉFLEXION
>
> Vous galérez ? C’est normal ! Au début vous pourriez peut-être y passer plus de 30 minutes ! Travaillez en groupe ou demandez des pistes !
>
> Vous tenez le bon bout !
>

> 🔍 DÉCOUVERTE
>
> Voici quelques pistes d’amélioration : variable de rotation modifiable dans l’éditeur, mettre ça dans des fonctions, récupérer le Trigger le plus proche ou même une double porte. 
> Pourquoi pas une porte s’ouvrant avec une touche ?
>

# Activités Supplémentaires
Vous avez réussi votre porte en Blueprint ? Super ! Non ? Réessayez ! Vraiment, c'est important pour la suite. Cela vous permettra de vous mettre dans une certaine logique.

Si ce n'est pas facile au début, c'est NORMAL ! Surtout si vous n'avez que très peu touché à la programmation ou un moteur de jeu. N'hésitez pas à demander de l'aide ou à me contacter si vous voulez vraiment le faire et que vous n'y arrivez pas.

Que vous ayez réussi, ou non - RETOURNEZ SUR LES BLUEPRITNS AU DESSUS -, je vous propose de plonger un peu plus dans la logique de programmation en Blueprint. Ceux qui voient encore les Blueprints comme un moyen utilisé par ceux qui ne savent pas coder... Vous n'avez pas totalement raison. Cela permet de se familiariser avec l'éditeur, ses fonctions, et fait directement écho au C++ (utilisé par Unreal Engine). N'oubliez pas que vous pouvez même créer vos Blueprints en C++ ! Ah et un conseil : Si vous le pouvez, travaillez à plusieurs, c'est mieux !

Je vous propose ainsi trois réalisations, en plus des bonus d'améliorations de la porte (sauf la récupération automatique du Trigger, cela peut être assez complexe au début à mettre en place).

- Un Blueprint de **SM_Lamp_Ceilling** ayant une **Point Light** ou **Spot Light** s'éclairant quand le joueur entre dans un **Triger Volume** ou utilise un **Input** de <a href="https://www.unrealengine.com/en-US/blog/input-action-and-axis-mappings-in-ue4">**Action Mappings (Project Settings)**</a>. Un peu d'aide par <a href="https://nerivec.github.io/old-ue4-wiki/pages/blueprint-light-switch-tutorial.html">ici</a>.
- Une maison **autonome** avec toutes les lumières s'éclairant une fois la personne passé la porte.
- Utiliser une **Timeline** pour rendre tout cela fluide et non instantané. Un éclairage progressive en soit. Attention, cela pourrait être utile d'utiliser la <a href="https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Timelines/index.html">Documentation</a> ou la vidéo de <a href="https://www.youtube.com/watch?v=v7bdcvGlgIg">WTFis</a>.

Si vous avez d'autres idées, ou ambitions, c'est le moment ! Mettez-les à l'épreuve ! Essayez même de nouvelles fonctions, pourquoi pas après tout ?

> 💭 RÉFLEXION
>
> Faites-vous plaisir ! C'est le moment ! Il n'y a pas de limite de temps... Ou presque ! Sinon, regardez la suite du Document !
>

# Pour aller plus loin
Nous avons vu les bases de l’éditeur, de son utilisation, et des Blueprints. Vous ne vous en rendez peutêtre pas compte, mais vous avait déjà fait un travail surhumain ! Et n’oubliez pas que, la limitation technique permet de développer la créativité. 😉

Si vous voulez vraiment vous lancer plus profondément dans ce moteur de jeu, je ne peux que vous recommander les vidéos de Ben Tristem sur Udemy concernant Unreal Engine. 
Ce dernier aborde autant le C++ que le Blueprints et les différents aspects de création d’un jeu tout en mettant au point des défis pour apprendre. 
De plus, si vous souhaitez apprendre gratuitement, Unreal Academy est un bon point, ainsi que pas mal de tutoriels sur YouTube. 
Vous pourrez trouver tous ces liens à la fin.

- <a href="https://academy.unrealengine.com/">Unreal Academy</a>
- <a href="https://www.youtube.com/watch?v=ZxY3TYqWN2o&list=PLqihHB3m2p02jzEK-YSAT2YDPOU9pDmKO">Kawaii Slender, Tutoriel Complet</a>
- <a href="https://www.udemy.com/unreale4/">Cours Udemy UE4 "officiel"</a>
- <a href="https://www.udemy.com/unrealcourse/">Cours Udemy UE4 par Ben Tristem et GameDevTV</a>
- <a href="https://www.udemy.com/unrealmultiplayer/">Cours Udemy UE4 Réseau par Ben Tristem et GameDevTV</a>
- <a href="https://www.mcvuk.com/development-news/10-things-you-didnt-know-you-can-do-with-unreal-engine-4/">Tips UE4</a>
- <a href="https://80.lv/articles/unreal-engine-4/">Inspiration et Tips pour Unreal Engine 4</a>

# Bonus
## Comment est-ce que l'on crée un jeu ?

Voici un modèle **très** simplifié que j'aime bien présenter : les étapes de création d'un jeu vidéo.

<br>

<div align="center">
<a id="UE_3"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/GameDev.png?raw=true" width="1000" height="" /></a>
</div>

<br>

Alors oui, cela ne correpondra sûrement pas à la méthodologie qu'utilise Ubisoft, mais le principe est là, surtout pour une Game Jam.

## Assets
Vous trouverez ici les [**Assets**][1] que j'ai jugé pertinent de vous donner.  
- Le **BP_Character_Master.uasset** vous permet d'utiliser tout personnage de Paragon (mais aussi d'autres en 3D) à récupérer sur le Marketplace, très simplement en peu de temps en créant un Child Blueprint, ou non. Presque toute la logique de déplacement et d'action à été mise en place, basé sur celui de Shinbi, asset gratuit fourni par Epic Games.
- Le **gitignore** vous permet de ne pas vous soucier des artefacts ou de ce que vous ajoutez dans le git. Il permet d'avoir un repo clean ! Testé et approuvé ! (Normalement...)
- Le **gitattribute** vous permet d'utiliser Git LFS pour gérer vos assets, les locks & co pour pouvoir travailler facilement à plusieurs sans conflit ! Il vous faut un serveur supportant LFS, à utiliser de pair avec <a href="https://github.com/SRombauts/UE4GitPlugin">ce plugin</a>.


# Crédits
Les images du moteur et du launcher ainsi que les assets de l'éditeur sont la propriétés d'Epic Games.\
Le contenu du cours a été écrit dans le cadre d'une présentation à des Coding Club et Hub d'Epitech Lyon.\
Merci à Thomas pour son aide à l'élaboration de ce cours !\
Si vous avez une question, un retour à me faire, ou autre, contactez moi via <a href="mailto:matthieu.eynard-longuet@epitech.eu">**matthieu.eynard-longuet@epitech.eu**</a>.

> ⚠️ INFORMATION
>
> D'autres sujets sont en cours d'édition, étant donné que ce Workshop fait partie d'une série de 3.
>

Pour plus d'informations : <a href="https://matthieu.ehanor.fr/">**https://matthieu.ehanor.fr/**</a>.

<br>

<div align="center">
<a id="UE_3" href="https://matthieu.ehanor.fr/"><img src="https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1/blob/develop/ressources_readme/Ehanor_Logo.png" width="150" height="" /></a>
</div>



[1]: https://github.com/Epitech-Lyon/Unreal-Engine-4---Workshop-1
