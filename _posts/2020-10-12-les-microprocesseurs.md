---
layout: post
title:  "Les Microprocesseurs"
author:
    - matheo.belleville@epitech.eu
categories: [ talk ]
image: assets/images/microprocessor/affiche.jpg
published: false
comments: false
---

## Un peu d'histoire

Quelques repères historiques :
- Avant 1970, ordinateurs non miniaturisés
- Après 1970, on commence à miniaturiser

La fabrication d'un microprocesseur est un processus industriel très complexe.

## Design

Von Newman et Harvard. Cependant la plupart des processeurs utlisent un peu des deux modèles.

### Von Neumann

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/01/Von_Neumann_architecture_fr.svg/1024px-Von_Neumann_architecture_fr.svg.png" alt="Von Neumann" width="40%"/>
**Fig 1**: Architecture de Von Neumann

### Harvard

<img src="https://upload.wikimedia.org/wikipedia/commons/6/69/Architecture_Harvard.png" alt="Harvard" width="30%"/>
**Fig 2**: Architecture de Harvard

## Les composants

Les composants d'un microprocesseur :
- Horloge
- Registres
- Cache
- Unités de calcul
- Jeux d'instructions

Il existe plusieurs familles de jeux d'instructions, par exemple :
- CISC
- RISC
- VLIW

Une liste de jeux d'instructions non exhaustive :
- x86 et x86_64 (CISC)
- ARM (RISC)
- Itanium (VLIW)
- Mips (RISC)
- PowerPC (RISC)
- s390X (CISC)

## Les jeux d'instructions

Les caractéristiques d'un jeu d'instructions :
- Nombre de bits
- Mots
- Endianness
- Instructions
- Assembler
- Appels systèmes

## Multithreading et types de processeurs

Les processeurs qui permettent de faire du multithreading:
- Processeur scalaires
- Processeurs superscalaires
- Processeurs vectoriels

## Indicateurs de performance

Les indicateurs de performance pour les processeurs sont nombreux :
- IPS : instructions par seconde
- nombre de transistor
- Flops : Floating Point Operation per second

Pour évaluer un microprocesseur, on peut également faire des benchmarks sur différentes tâches plus haut niveau (le plus réaliste).

## Loi de Moore

La loi de Moore est une loi empirique sur lévolution de la puissance de calculs et de la complexité du matériel informatique.

## Conclusion

Cet article avait pour but de présenter les microprocesseurs de manière simple et accessible. Plusieurs concepts sont nécessaires pour bien entrer cet univers complexes, parmi lesquels :
- Design : Von Neuman, Harvard
- Les jeux d'instructions et leur type (ou famille de jeux d'instructions).
- les indicateurs de performances
- le multithreading

