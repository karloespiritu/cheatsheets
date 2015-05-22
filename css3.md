---
layout: page
title: CSS3 Animations
permalink: /css3/
---

```css
.element {
  animation: pulse 5s infinite;
}

@keyframes pulse {
  0% {
    background-color: #001F32;
  }
  100% {
    background-color: #D41368;
  }
}
```

## Sub-properties

```css
.element {
  animation-name: stretch;
  animation-duration: 1.5s;
  animation-timing-function: ease-out;
  animation-delay: 0;  //Specifies a delay for the start of an animation
  animation-direction: alternate;  //Specifies whether an animation should play in reverse direction or alternate cycles
  animation-iteration-count: infinite;
  animation-fill-mode: none;
  animation-play-state: running;
}

```