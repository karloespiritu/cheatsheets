---
layout: page
title: Flexbox
permalink: /flexbox/
---

## Create a Flex Container

```css
.flex-container {
   display: flex;
}
```

## Row layout

```css
.flex-container {
   display: flex;
   flex-direction: row;
}
```

## Column layout

```css
.flex-container {
   display: flex;
   flex-direction: column;
}
```

## Align Layout to Top

```css
.flex-container {
   flex-direction: column; /* row if horizontal layout */
   justify-content: flex-start;
}
```

## Align Layout to Left

```css
.flex-container {
   display: flex;
   flex-direction: row;
   justify-content: flex-start; /* align-items: flex-start; if column */
}
```

## Align Layout to Right

```css
.flex-container {
   display: flex;
   flex-direction: row;
   justify-content: flex-end; /* align-items: flex-end; if column */
}
```

## Center everything

```css
.flexcontainer {
   display: flex;
   flex-direction: row; /* works wth 'column' as well */
   align-items: center;
   justify-content: center;
}
```

## Grow a flex item X times as big as other flex items

```css
.big-item {
   /* This will be twice as big as the small item. */
   flex: 2 0 0;
}
.small-item {
   flex: 1 0 0;
}
```

## Wrap flex items into multiple rows

```css
/* On the flex container */
.flex-container {
   display: -webkit-flex;
   display: flex;
   align-items: center;
   justify-content: center;
   /* You can set flex-wrap and flex-direction individually */
   flex-direction: row;
   flex-wrap: wrap;
   /* Or do it all in one line with flex flow */
   flex-flow: row wrap;
   /* tweak the where items line up on the row */
   /* valid values are: flex-start, flex-end, space-between, space-around, stretch */
   align-content: flex-end;
}
```

## Wrap flex items into multiple columns

```css
.flex-container {
   display: -webkit-flex;
   display: flex;
   align-items: center;
   justify-content: center;
   flex-flow: column wrap;
   align-content: stretch;
}
```

## Remove the space from wrapped rows or columns

```css
.flexcontainer {
   display: flex;
   align-items: center;
   justify-content: center;
   flex-flow: column wrap;
   align-content: center;
}
```

Reference:

[http://www.sketchingwithcss.com/samplechapter/cheatsheet.html](http://www.sketchingwithcss.com/samplechapter/cheatsheet.html)
