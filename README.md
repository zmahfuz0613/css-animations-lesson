# CSS3 ANIMATIONS

You know a little bit how to move stuff around with JavaScript.... now let's learn how to make it move around with CSS.

### Learning Objectives

- Compare traditional hand-drawn keyframe animation and CSS animations
- Use the `animation` property to animate elements
- Use the `transform` property to change elements
- Implement different values for the `transform` property to describe their effect
- Recognize the parts of keyframe syntax
- Deconstruct the description of an animation to assemble proper CSS syntax

## Transitions 

**Transitions** let us tell the browser how to change a property over time. You'll commonly see the `transition` property used on `:hover` and `:focus` states, as we talked about last week.

However, with `:hover` and `:focus`, we were mostly changing things like background color, font color, etc. Transition can be used with many more properties.

### ✨ Follow along in this [Codepen](http://codepen.io/jlr7245/pen/zZVJyL?editors=1100)!!

#### 📚 For reference:

The `transition` property is shorthand for a number of other properties -- like `border` is shorthand for `border-color`, `border-width`, etc. The syntax goes like this:

```css
transition: property duration timing-function delay;
  /* - property: which property the transition effect is for */
  /* - duration: how many seconds or milliseconds the transition effect takes */
  /* - timing-function: specifies the "speed curve" of the transition effect */
  /* - delay: defines with the transition effect will start */
```

So, if we were trying to write a transition rule that smoothly changes the background color over 2 seconds starting 1s after the action that causes the transition, we'd write:

```css
transition: background-color 2s ease 1s;
```

### Not all properties are "transitionable" or "animatable". 

Here's a table of the most common animatable & non-animatable properties. (It's not an exhaustive list; head over to [W3Schools](https://www.w3schools.com/cssref/css_animatable.asp) for the full list.)

| Animatiable                                                  | Not animatable                              |
|--------------------------------------------------------------|---------------------------------------------|
| `background-color`, `background-position`, `background-size` | `background-image`, `background-blend-mode` |
| `top`, `bottom`, `left`, `right`                             | `position`                                  |
| `height`, `width`, `min-height`, `min-width`                 | -                                           |
| `margin`, `border`, `padding`                                | `box-sizing`, `border-image`                |
| `opacity`, `visibility`                                      | `display`                                   |
| most text & font properties                                  | `font-family`                               |
| -                                                            | `float`, `clear`                            |


### Transitions are pretty cool.

But they have some limitations, at least in the way we're using them here. What if we don't want to have to hover over the circle to get it to move? What if it should move when the page loads? We could feasably force that with JavaScript and a `setTimeout`, but that puts us back in the world of DOM manipulation. There's an easier way...

## Keyframes & the `animation` property

### What is a "keyframe"?

![keyframes example](./assets/keyframes.jpg)

Keyframes are a common animation concept, usually found in hand-drawn animation. In the above image, the figures in grey are **keyframes** - they define the starting, ending, or middle point of a smooth transition. The other drawings are **in betweens** - they don't have to be drawn on a storyboard, because the animator can assume what they will look like without a visual reference.

In web-based animations, keyframes work the same way - they represent the beginning, ending, or midpoint state of the element being animated. However, our in betweens will be generated by code, instead of being filled in by hand later.

The `transition` property allows us to define a beginning and end point for a state change. However, sometimes you'll want to have an element move through multiple states during an animation. That's where the CSS keyframes rule comes in.

### 📚 Keyframe Syntax

Keyframe syntax uses `@`, just like media queries, but it looks a little different inside. Let's take a look at the bare bones of a keyframe rule:

```css
/* keyframes keyword, animation name */
@keyframes ANIMATION-NAME {
  /* description of the animation */
  0% {
    /* the beginning state of the animation */
    property: first-value;
  }
  50% {
    /* the middle state of the animation */
    /* you can have as many mid-points as you want,
       at whatever percentages you want. */
    property: second-value;
  }
  100% {
    /* the ending state of the animation */
    property: third-value;
  }
  /* In order for animations to happen smoothly, you must
     animate the same property at every animation !! 
     For ex, to smoothly animate a circle from left to right,
     you wouldn't do `left: 0%;` and then `right: 0%;`. You have
     to keep animating `left`. */
}
```

And here is how you apply an animation rule to a CSS class:

```css
.animate-me {
  animation: NAME duration timing-function delay animation-iteration-count direction fill-mode play-state;
}
  /* This is sort of like the transition property shorthand: each of these does a different thing. */
  /* - animation-name: specifies the name of the keyframe rule */
  /* - animation-duration: specifies the number of seconds or milliseconds */
  /* - animation-timing-function: specifies the "speed curve" of the animation */
  /* - animation-delay: specifies a delay before the animation will start */
  /* - animation-iteration-count: specifies how many times an animation should be played */
  /* - animation-direction: specifies whether or not an animation should be played in reverse on alternate cycles */
  /* - animation-fill-mode: specifies what values are applied by the animation outside the time it is executing */
  /* - animation-play-state: specifies whether the animation is running or paused */
    
```

(definitions from [W3Schools](https://www.w3schools.com/cssref/css3_pr_animation.asp))

### ✨ Follow along in the next [Codepen](https://codepen.io/zanewhit/pen/YzqaqKR)!!

## Transforms

Transforms allow you to rotate, skew, and pivot your HTML elements in 3D space! While you'll still be rendering your result on a 2D canvas - your computer screen - you can still move your object around like it were a physical object. `transform` is just one property, but it has about 20 possible values. 

A neat thing about transforms is that they affect not only the element they're applied to but also the element's children.

### ✨ Let's see this in action! Follow along in [this codepen](http://codepen.io/jlr7245/pen/evwaNK?editors=0100)


There are four main types of transformations: skew, rotate, translate, and scale. These demos all use them in the context of animation, but you can also just use them on an element -- this is probably most common with rotate. (Want text a little bit slanted? That's `transform: rotate(10deg);`)
<details>
<summary> 📚 Transform Demos </summary>

- **Skew**: Defines a skew transformation -- i.e. changing a box into a parallelogram, etc.
    - [✨ **Example codepen** ✨](http://codepen.io/jlr7245/pen/JWQQYX?editors=0100)
    - Skew does not have a z-axis value.
- **Rotate**: Rotates an element along the given axis. 
    - [✨ **Example codepen** ✨](http://codepen.io/jlr7245/pen/MpMdrP?editors=0100)
    - Bonus: Try uncommenting the `transform-style: preserve-3d;` line (ln 104 of the CSS) and see how that changes the rotations. Notice anything interesting?
    - Bonus 2: The [backface visibility](https://www.w3schools.com/cssref/css3_pr_backface-visibility.asp) property helps with rotations, if you don't want to be able to see the text backward through the rotated element's backface. [Here are some examples.](https://designmodo.com/backface-visibility-css-animation/)
    - Confession: the `rotate3d()` demo is mostly from [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate3d) and apparently has something to do with cartesian coordinates, which are beyond me.
- **Translate**: Moves an element to the left & right, or top & bottom, or alters its height from the z-plane.
    - [✨ **Example codepen** ✨](http://codepen.io/jlr7245/pen/evwaNK?editors=0100)
    - "Why not just animate left and right?" Translate actually has better performance, even at a small scale, since it doesn't have to talk to the rest of the elements on the page. It can also be used on any elements, even ones with `position: static;` that setting left and right on won't have any effect over.
- **Scale**: Grows and shrinks an element along the x, y, or z axis.
    - [✨ **Example codepen** ✨](http://codepen.io/jlr7245/pen/QpXXEz?editors=0100)
    - `scaleZ(z)` is most frequently used with `translateZ(z)`. [Read here](https://tympanus.net/codrops/css_reference/scalez/) for more information.

Some of these demos have been paired with an extra value, `perspective(n)`. You can read more about CSS perspective [here](https://css-tricks.com/almanac/properties/p/perspective/), and check out [this illustration](http://codepen.io/HugoGiraudel/pen/GLbca). Essentially, it describes how many pixels away from the z-plane the user is. (Sound confusing? Me too. Just play around with it and you'll figure it out.)

> Sidenote: Usually when writing CSS animations, you'll see `-webkit-` and `-moz-` prefixes. Those are called vendor prefixes. Some of the animations we're doing are so cutting edge, that they haven't been formally adopted by all browsers. In cases like this, you'll have to call the same value multiple times with vendor-specific prefixes to make sure that Chrome(`-webkit-`), Firefox(`-moz-`), IE(`-ms-`), and Opera(`-o-`) all display the animation correctly. Always leave a non-prefixed call in as well - as these properties are formally adopted, the need for the vendor prefix will disappear, as will its support. Not sure if you need a prefix? Go to Can I Use and search for the CSS property you want to use - you'll receive a detailed breakdown of what browsers support it.

</details>

# 💥 Exercise

### Practice with turning drawings into animations using keyframes!

- Create a fork of [this codepen](http://codepen.io/jlr7245/pen/BWgvxo?editors=1100).
- Write out the steps you think the animation will need.
- Make the animation happen! 

**Note**: You won't need to use the `transform` property for this lab
