---
date: 2017/10/08
title: Paint Splatter Effect
layout: post
---

As has been mentioned, the paint splatter effect is a core part of the overall aesthetic of the game. The algorithm is quite simple, and is adapted from [Zack Bell.](https://zackbellgames.com/2015/03/31/effects-blood-splatter/)

For starters, you can find an example of what the effect looks like from one of my [first posts](/?posts%2F2017-09-11-dev-snapshot) and from this [demo page](https://alan-luo.github.io/demos/demos/splat.html). The algorithm is essentially the same.

![concept 1](/assets/img/splatters.png)

Let's break down this algorithm.

For simplicity, we're going to look at the Javascript implementation. The linked demo uses the Canvas API, but for explanation purposes, we're going to replace all draw functions with generic draw functions so that the code is more easily translatable into other languages.

For reference, here are the helper functions that we use:

```
function drawCircle(x, y, r) {
  ctx.beginPath();
  ctx.arc(x, y, r, 0, 2*Math.PI);
  ctx.fill();
}
function random_range(min, max) {
  return Math.random()*(max-min)+min;
}
```

Now, let's model the splatter effect. Take a look at the screenshot above. Our ideal paint splatter is splotchy and irregular, and occasionally has thin streaks that go far out. We can model each streak as a bunch of circles in a line going outward from the splat center, getting smaller each time. To get our full splatter, we just put a bunch of these streaks together.

We're going to create a function `makeSplat` which will take in a `startx` and `starty` and will create a streak at the given point.

```
function makeSplat(startx, starty) {
  //CREATE
  let image_scale = Math.random()*0.66+0.33;

  let moveDir = Math.random()*360;
  let moveSpd = random_range(3, 12);

  let sizeChange = random_range(image_scale/10, image_scale/3);
  
  ...
}
```

We declare `image_scale` as a random float from 2/3 to 1. It creates size variation in our splats. `moveDir` and `moveSpd` determine in what direction and how far each circle will move. `sizeChange` is a friction-like variable that determines how much each successive circle changes by.

Now, we add a step function:

```
function makeSplat(startx, starty) {
  //CREATE
  let image_scale = Math.random()*0.66+0.33;

  let moveDir = Math.random()*360;
  let moveSpd = random_range(3, 12);

  let sizeChange = random_range(image_scale/10, image_scale/3);

  //STEP
  let destroyed = false;
  let x = startx; 
  let y = starty;
  ctx.globalAlpha = 0.6;
  let startRadius = random_range(10, 20);
  while(!destroyed) {
    drawCircle(x, y, startRadius*image_scale);

    image_scale-=sizeChange;

    if(moveSpd>0) {
      ctx.globalAlpha -= random_range(0.05, 0.1);
    }

    moveSpd*=0.90;

    x+=moveSpd*Math.cos(moveDir);
    y+=moveSpd*Math.sin(moveDir);

    if(image_scale<0) {
      destroyed = true;
    }
  }
  
}
```

We start off by declaring `x` and `y` variables, which store the position of the next circle being drawn. We also declare a `startRadius` for the size of the first circle, and change the `globalAlpha` of our drawing. This is a canvas-specific effect which is used to give semitransparency to each splatter.

In the step function, we're just going to keep translating, scaling, and drawing a circle until the scale gets too small. Each step, the move speed decreases a little bit exponentially. We also make the alpha lower (make the transparency greater) each step to give a faded out effect.

That's our completed `makeSplat` function. All we need to do now is make each splatter:

```
function makeSplatter(x, y) {
  ctx.fillStyle = `hsl(${Math.random()*360}, 70%, 50%)`;
  
  let bound = random_range(4, 12);
  for(let i=0; i<bound; i++) {
    makeSplat(x+Math.random()*16, y+Math.random()*16);
  }
}
```

The `makeSplatter` function will create a full paint splatter at position `(x, y)`. In this case, we just declare the fill style to be a random color, then set a total number of splats from 4 to 12. We then create that number of splats at the desired point, with a bit of location variation for each one.

That's it! That's the full effect.

There's a number of ways to optimize this effect. For instance, the splats still look a bit inorganic. I'd like for there to be more crazy long streaks. This comes down to a matter of tuning variables. It's also not totally natural for the circles to move out in straight lines. By adding a delta theta to each step, you could easily make the circles curve.

In either case, I will continue tuning the effect, and I'll write an update if I make any major changes.