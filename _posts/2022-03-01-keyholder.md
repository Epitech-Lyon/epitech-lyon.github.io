---
layout: post
title:  "Keyholder: a twin-stick top-down shooter made with Godot"
author:
    - pascal.betti@epitech.eu
    - rayan.djellabi@epitech.eu
categories: [ experience ]
image: assets/images/keyholder/poster.png
published: true
comments: false
---

Keyholder (previously named The Key of Success) was made during the weekend from February the 11th to the 13th of 2022, for an Epitech Jam which is sort of a contest in which you have to produce a game or a software fitting an imposed theme in ~48 hours.
This time, the theme of the jam was "Success", which is a very large theme that could be interpreted in many ways:

- First off, success defines the act of achieving, reaching your objectives. But success may require taking risks.
- Secondly, we settled on two widely used symbols that also fit to describe success: the key (for exemple the key of success), which represents potential, and the door, that represents an objective to reach.

We took example on both of these ideas for our game.

## Why Godot?

First off, what even is Godot? Godot is a free, open-source and extremely light weight yet very powerful and, while hard to master, quite easy to learn engine, and these reasons made it one of the favorite tools used for game jams, especially for 2D entries, but Godot is equally able to produce quality 3D games.

To this day we have a year of experience with the engine and making 2D games, and since we settled with doing a top-down 2D shooter for this jam, Godot was our an evident choice.
 
If you'd like to try Godot yourself, you can download it from its [official website][1].

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

The theme was revealed and we went through the ideation process. We each gave one or more idea that we discussed together. Some were great, some were terrible.

Due to past experiences, we were careful to fully lay out what the game was going to be. Everyone had to know exactly what the game was about and what they had to do, because we've had problems in past jams where some members of the team didn't fully know what they needed to do, so they did nothing.
When choosing what type of game to make, it's important to keep in mind that you only have the weekend to make it. A common mistake is to try to make something too ambitious.

In the evening, we began development on a twin-stick top-down shooter where the player is carrying a key that enemies want to steal from them. When the player doesn't have the key, it slowly dies down. The goal is to prevent the key from breaking until the door is open.

Our principal inspiration was Yoshi's Island, in which Yoshi has to protect Baby Mario.

### Saturday

Saturday is when the core part of the game was made. From the beginning, we cared **a lot** about the atmosphere of the game. We planned for the game to take place in some sort of temple. That's why one of the first things we focused on was the lighting.

![Keyholder on Saturday afternoon](https://i.imgur.com/z8ev36d.jpg)

The character always emits blue light that travels very far and creates big shadows on the pillar, so that the player can know its position without even looking at it.

The key and the door are the only yellow elements, clearly stating both of the objectives. The key emits a strong yellow light that loses its power and stability as the key loses health.

The door starts almost completely transparent, and slowly fades in, emitting more and more light until it becomes really bright and a white beam of light comes out of it, announcing the end of the level.

We also completed some of the base mechanics: the player can move and shoot, carrying the key.
The enemies can die *and* steal the key from the player.

For now though, there is no way to win the level and the player and enemies are both represented by squares.

### Sunday

![Keyholder at the time of submit](https://i.imgur.com/xWHU8Vo.png)

On this last day, we implemented a way to win, and added 2 more levels.
We also added graphics for the player, the enemy, and the portal they come out of. The enemies also now have a purple aura around them to make them easier to spot.

We worked on some feedback features, like screenshake when you shoot and kill an enemy, a slight movement of the camera following the mouse, and of course **sound and music**!

These may not seem like much, but they are actually really important to have the game feel responsive and impactful. Games without feedback can often feel unfinished, cheap or even poorly made.

With a few hours left, we designed an intro sequence with a few dialogues and camera movements, fixed a few bugs and crashes, and we ended up with a game we were really satisfied with!

### Post-jam improvements

After the jam ended, we added a few features. First off, we thought the game was a bit too easy. So we added special, bigger enemies that take *two* hits to kill! We also reduced the health of the key by half, so that it would last only 15 seconds out of the player's hands, instead of 30.

Yay! The game is now challenging. But sadly there are only 3 levels, so it's pretty short, and there's no way to showcase how much of a pro gamer I am.
Worry not, we added an endless mode! This mode features only one level, but with no door. The only goal is to keep the key intact for as long as possible. A score counter was added for everyone to flex their g@mer skills with proof.

### Please try our game!
If you'd like to download our entry, please go to our itch.io page! Do not hesitate to give us your feedback on Itch as well.

Itch :  https://galerianstudio.itch.io/keyholder

## Conclusion

This jam went pretty well! We made a game that is both fun to play and visually attractive, all while having fun (and dancing while programming).
We made every choice consciously while taking care not to reproduce past mistakes, and it definitely shows!

[1]: (https://godotengine.org/)
[2]: (https://github.com/Spacelenin)
[3]: (https://github.com/Gr1moire)
[4]: (https://github.com/Imnibis)
[5]: (https://github.com/STMiki)
[6]: (https://github.com/DorianCollin)
[7]: (https://github.com/matmansn)
[8]: (https://github.com/LorienEpitech)