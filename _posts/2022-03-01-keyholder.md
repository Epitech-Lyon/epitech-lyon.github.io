---
layout: post
title:  "Keyholder: a twin-stick top-down shooter made with Godot"
author:
    - pascal.betti@epitech.eu
    - rayane.djellabi@epitech.eu
categories: [ experiment ]
image: assets/images/keyholder/poster.png
published: true
comments: false
featured: true
---

**Keyholder** was made during the weekend from February the 11th to the 13th of 2022, for an Epitech Jam which is sort of a contest where you have to produce a game or a software fitting an imposed theme in ~48 hours. This time, the theme of the jam was "Success", which is a very broad theme that could be interpreted in many ways:

> An Epitech Jam which is sort of a contest where you have to produce a game or a software fitting an imposed theme in ~48 hours.

- First off, success defines the act of achieving, reaching your objectives. But success may require taking risks.
- Secondly, we settled on two widely used symbols that also fit to describe success: the key (for exemple the key of success), which represents potential, and the door, that represents the objective to reach.

We took example on both of these ideas for our game.

## Why Godot?

[Godot][10] is completely free and open source under the very permissive [MIT license][11]. No strings attached, no royalties, nothing. The users' games are theirs, down to the last line of engine code. Godot's development is fully independent and community-driven, empowering users to help shape their engine to match their expectations. It is supported by the [Software Freedom Conservancy][12] not-for-profit.

Since Godot is free, open-source and quite easy to learn, it is a very popular tool among Epitech Game Jam authors. It was our pick for the challenge.

## The team

Our team, Galerian Studio, fluctuates between 3 to 7 members depending on the project.

For this one, we were 7, namely:
- [Nolan Kijas][2]
- [Pascal Betti][3]
- [Rayane Djellabi][4]
- [Michael Veillet-Guillem][5]
- [Dorian Collin][6]
- [Mathis Clanche][7]
- [Lorien Remy][8]

## Development process

### Friday

The theme was revealed and we went through the ideation process. Each one of us gave one or more ideas that we discussed together. Some were great, some were terrible - for the sake of your minds, I won't expose them in this post.

Due to our past experiences, we were careful to fully lay out what the game was going to be. Everyone had to know exactly what the game was about and what they had to do, because we've had problems in past jams where some members of the team didn't fully understand what they needed to do, so they did nothing! When choosing the kind of game to develop, it's important to keep in mind that you only have a weekend to do it. A common mistake is being too ambitious.

In the evening, we began the development on a twin-stick top-down shooter where the player is carrying a key that enemies want to steal. When the player doesn't have the key, it slowly dies down. The goal is to prevent the key from breaking until the door opens.

Our principal inspiration was Yoshi's Island, in which Yoshi has to protect Baby Mario.

### Saturday

The core part of the game was made in Saturday. From the beginning, we cared **a lot** about the atmosphere of the game. We planned for the game to take place in some sort of temple. That's why one of the first things we focused on was the lighting.

![Keyholder on Saturday afternoon]({{ site.baseurl }}/assets/images/keyholder/z8ev36d.jpg)
<small> Fig 1. </small>

The character always emits blue light that travels very far and creates big shadows on the pillar, so that the player can know its position without even looking at it. The key and the door are the only yellow elements, clearly stating both of the objectives. The key emits a strong yellow light that loses its power and stability as the key loses health (see Fig. 1).

The door starts almost completely transparent, and slowly fades in, emitting more and more light until it becomes really bright and a white beam of light comes out of it, announcing the end of the level. We also completed some of the base mechanics: the player can move and shoot, carrying the key. The enemies can die *and* steal the key from the player.

For now though, there is no way to win the level and the player and enemies are both represented by squares.

### Sunday

![Keyholder at the time of submit]({{ site.baseurl }}/assets/images/keyholder/xWHU8Vo.png)
<small> Fig 2. </small>

On this last day, we implemented a way to win, and added 2 more levels.
We also added graphics for the player, the enemy, and the portal they come out of. The enemies also now have a purple aura around them to make them easier to spot (see Fig. 2). 

We worked on some feedback features, like screenshake when you shoot and kill an enemy, a slight movement of the camera following the mouse, and of course **sound and music**!

These may not seem like much, but they are actually really important to have the game feel responsive and impactful. Games without feedback can often feel unfinished, cheap or even poorly made.

With a few hours left, we designed an intro sequence with a few dialogues and camera movements, fixed a few bugs and crashes, and we ended up with a game we were really satisfied with!

### Post-jam improvements

After the jam ended, we added a few features. First off, we thought the game was a bit too easy. So we added special, bigger enemies that take *two* hits to kill! We also reduced the health of the key by half, so that it would last only 15 seconds out of the player's hands, instead of 30.

Yay! The game is now challenging. But sadly there are only 3 levels, so it's pretty short, and there's no way to showcase how much of a pro gamer I am.
Worry not, we added an endless mode! This mode features only one level, but with no door. The only goal is to keep the key intact for as long as possible. A score counter was added for everyone to flex their g@mer skills with proof.

### Please try our game!

If you'd like to download our entry, please go to our itch.io page! Do not hesitate to give us your feedback on Itch as well.

Itch :  [click here to play][9]

## Conclusion

This jam went pretty well! We made a game that is both fun to play and visually attractive, all while having fun (and dancing while programming).
We made every choice consciously while taking care not to reproduce past mistakes, and it definitely shows!

## References

- [https://sfconservancy.org/][12]
- [Godot Engine Official Website][1]
- [https://galerianstudio.itch.io/keyholder][9]


[1]: https://godotengine.org/
[2]: https://github.com/Spacelenin
[3]: https://github.com/Gr1moire
[4]: https://github.com/Imnibis
[5]: https://github.com/STMiki
[6]: https://github.com/DorianCollin
[7]: https://github.com/matmansn
[8]: https://github.com/LorienEpitech
[9]: https://galerianstudio.itch.io/keyholder

[10]: https://github.com/godotengine/godot
[11]: https://godotengine.org/license
[12]: https://sfconservancy.org/
