# CSS ANIMATIONS!!!!!

You know a little bit how to move stuff around with JavaScript.... now let's learn how to make it move around with CSS!!!

### Learning Objectives

- Understand how traditional hand-drawn keyframe animation and CSS animation relate
- Use the `animation` property to animate elements
- Use the `transform` property to change elements
- Recognize the different values for the `transform` property and see what they do
- Recognize the parts of keyframe syntax
- Analyze a description of an animation and understand at a high level what steps would be needed to reproduce it

## Transitions Redux

**Transitions** let us tell the browser how to change a property over time. You'll commonly see the `transition` property used on `:hover` and `:focus` states, as we talked about last week.

However, with `:hover` and `:focus`, we were mostly changing things like background color, font color, etc. Transition can be used with many more properties.

### ✨ Follow along in this [Codepen](http://codepen.io/jlr7245/pen/zZVJyL?editors=1100)!!

#### 📚 For reference:

The `transition` property is shorthand for a number of other properties -- like `border` is shorthand for `border-color`, `border-width`, etc. The syntax goes like this:

```css
transition: property duration timing-function delay;
/* property: which property the transition effect is for
   duration: how many seconds or milliseconds the transition effect takes
   timing-function: specifies the "speed curve" of the transition effect
   delay: defines with the transition effect will start */
```

So, if we were trying to write a transition rule that smoothly changes the background color over 2 seconds starting 1s after the action that causes the transition, we'd write:

```css
transition: background-color 2s ease 1s;
```


## Keyframes & the `animation` property

- Keyframes as an animation concept
- Keyframe syntax
- `animation` property syntax -- diagram on board
- putting it all together -- we code a bouncing circle together & play around with the different animation property values (reverse, repeat, time, etc.)

# Lab 1

- Work in groups
- Each group gets an index card with a series of keyframes drawn on it
- They get some kind of starter CSS and have to write the animation
- will include: applying syntax, looking up documentation
- Include links to some documentation

## Transforms

- Go over the different families of transform properties
    - translate
    - scale
    - rotate
    - skew
- concept: when you rotate an element, everything inside the element also rotates
- we do together:
    - rotate a box with text in it first
    - rotate a box with a circle in it
    - rotate multiple boxes
    - hey look, we built a solar system

# Lab 2

- They try to add one or two planets to the solar system