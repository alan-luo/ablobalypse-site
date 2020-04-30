---
title: Development Snapshot (September 11, 2017)
date: 2017/09/11
layout: post
---

This is the current state of development as of September 11, 2017. This is being written just after the launching of this blog. Here's a gif!

![first gif](/assets/img/firstgif.gif)

I have pretty much the entire design thought out, from aesthetic to gameplay. Of course, many of the subtle details are vulnerable to change - but the vision is there. I'm going to post some concept art soon.

The basic physics and mechanics have been established in Unity. I've create a state engine to manage my jump physics, which now feel clean and responsive. I've also created basic entities for the player, enemies, and bullets. I've added also added a shiny cool paint splatter effect.

Unfortunately, that paint splatter effect is causing some problems. Functionally, it works just fine, but processing the texture seems very slow in Unity. Based on some reading, I think it's an issue I can't resolve.

To accomplish the paint effect, I'm updating a texture the size of the level which is masked using sprites that represent platforms. In theory, this means that splatter effects only need to be processed once, and the splatter object can be destroyed, while the resulting pixels remain on the screen. I'd like to use this effect to give a sharp, colorful vibe to my game.

However, it seems that Unity processes texture updates on the CPU and then uploads them to the GPU. The CPU and GPU individually are fast enough to process the texture, however, the pipeline between the two has a bandwidth issue and cannot handle large texture updates.

I've reached a crossroads. I can either redo the vision of my game and continue using the engine I'm more familiar with (Unity), or I can ditch the engine altogether while I'm still early in the project and port the whole thing over to Game Maker, which I have never used before.

I've decided that the coding part of this whole development process will most likely be the easiest part, as it is the part I am most adept at. Since I am better at coding and worse at design, it makes sense to preserve the sanctity of my cohesive design at the expense of programming efficiency.

Next steps: post concept art, finish making blog (as of writing, this post is sitting on a Markdown file on my computer), port current demo over to Game Maker.