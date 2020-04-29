---
title: Paradigm Postmortem
date: 2017/10/01
layout: post
---

I'm writing this article to talk about a major decision I reached at an early stage of development. A few weeks ago, I made the decision to scrap all the work I had done in Unity and start from scratch with Game Maker. I did so on the basis of an aesthetic decision. Essentially, I realized that I would be unable to accomplish the exacct aesthetic I was looking for in Unity.

When I made the decision to switch, I made the following assumptions:

- Learning Game Maker would be easy.
- The aesthetic was core enough to the game that I couldn't give it up.

In this postmortem, I want to evaluate how these decisions affected my development cycle.

**On Aesthetic**

It's hard to evaluate whether or not I made the correct decision in terms of artistic integrity when it comes to maintaining the aesthetic. There are no worlds where I proceed to follow both the path where I preserve artistic integrity and the path where I forsake it. The best I can do is draw from my personal analysis of specific games.

I believe that every best indie game maintains a consistent aesthetic that promotes a cohesive experience. It is this cohesion that allows low budgets to stand out ad unique and energizing rather than as cheap and reused.

For instance, consider [Botanicula](http://botanicula.net/) by Aminata Design. The characters are static and barely animated, and the main enemy is essentially a blob of spray paint. However, each character has a rich personality which can be experienced through gameplay. 

This is accomplished through the use of music, sound, and gameplay. The [music](https://www.youtube.com/watch?v=eZGJ-_zfMtY) is playful and makes liberal use of childish sounds and samples. The game is a point-and-click adventure, a genre that encourages puzzle-solving in an organic and exploration-based manner. The result is that playing Botanicula feels like living childhood again. The game uses its graphics, music, and gameplay as a single expressive unit.

Another such example is [Thomas was Alone](http://www.mikebithellgames.com/thomaswasalone/) by Mike Bithell. The game tackles the task of bestowing personality on a set of colored rectangles. Again, the music and gameplay contribute to this. 

The characters are presented as AI, making rectangles the simplest tangible manifestation. The music is procedural and electronic, giving the player the same sense of estranged wonderment of the characters. The core gameplay mechanic involves the different jump properties of each character. In this way, the crutch of using geometric characters is turned into a creative technique.

Thomas Was Alone also features a narrator that fills in certain voices, but I ascertain that the personality of each character would be just as clear without narration.

There are, of course, counterexamples. In many cases, a game's aesthetic is unimportant to the experience of the game. Other times, it arises organically out of the development process.

[Minecraft](https://minecraft.net/en-us/) would be a canonical example of the former. While dated graphics have come to symbolize Minecraft, the game was not designed with visuals or music in mind. In fact, the game wasn't even designed with game in mind. It was just an experiment that happened to get really popular. Music and graphics were added in post. Neither is particularly important to the gameplay, as evidenced by the popularity of texture packs and reskins in Minecraft.

Most games that come out of Ludum Dare are instances of the latter. Occasionally, games made during the 48-hour game jam get turned into full, publishable projects. Considering that the goal of these games is usually to simply be completed within 48 hours, graphics and music are usually retrofitted to suit the initial gameplay design. [Titan Souls](http://store.steampowered.com/app/297130/Titan_Souls/) is an example of such a game. Just compare it to the original [LD28 version](http://ludumdare.com/compo/ludum-dare-28/comment-page-5/?action=preview&uid=7984).

**On Game Maker**

My decision to learn Game Maker was partly motivated by the impression that Game Maker was a straightforward and simple engine to learn. While this impression is true, and is advertised on the company website, certain aspects of learning Game Maker nevertheless posed certain difficulties.

For instance, Game Maker uses a proprietary scripting langauge called GML. Even though C#, which Unity uses, is in many ways more complex than GML, I had already used C# before. This meant that learning Unity was a simple manner of learning the API. Even though the engine was more complex, I had a more solid baseline going into it. In addition, Unity is built on a 3D coordinates system, which I already had experience working in through OpenGL and WebGL projects. On the other hand, GML uses a completely sprite-based 2D system.

This meant that the main difficulties in learning Game Maker came not from technical shifts but from paradigm shifts; in moving my thinking from C# to GML and from 3D to 2D. (Unity's 2D system actually renders 2D objects in 3D space.) The result was that while it was not difficult to learn the engine, it still took longer that I initially thought it would.

It didn't help that while all this was going on, I was sick and had a lot of other work on my plate. I thought I would be able to crunch through the Game Maker tutorials in a weekend or so. In theory, if I had a free weekend, I would have been able to do so. However, I ended up packing each weekend with some activity, and never found the time. 

**Conclusion**

My main takeaway from this whole experience is that in the future, I need to take deadlines and workload into better cosideration to evaluate more realistic expectations. It took much longer than I thought it would to learn Game Maker. While some of this can be ascribed to the engine, the fact remains that I should not have assumed the simplicity of the engine to begin with. Even if Game Maker used a more popular scripting language, I should have assumed that the engine would have had some nuances down the road that would have inhibited development anyway.

The other issue was that I simply bit off more than I could chew. I did not accurate evaluate my workload and the size of the projects I could undertake. This is a mistake of project management more than anything. Considering my other classes, it should have been obvious to me that learning Game Maker would be a daunting task, even if the engine were simple.

In the future, I should reserve time outside of normal work hours for learning an engine, and recalculate project times based on that. I should also take those increased times into greater consideration when considering my own workload. My lack of sleep has led me to be sick for three weeks. I think that this experience has been a good way to force me into better project management habits.