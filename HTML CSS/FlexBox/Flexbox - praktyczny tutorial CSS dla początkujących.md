https://www.youtube.com/watch?v=o_GnXwio5Hs
https://flexboxfroggy.com/

#flexbox #youtube 


## `justify-content`
aligns items horizontally:
-   `flex-start`: Items align to the left side of the container.
-   `flex-end`: Items align to the right side of the container.
-   `center`: Items align at the center of the container.
-   `space-between`: Items display with equal spacing between them.
-   `space-around`: Items display with equal spacing around them.


## `align-items`
aligns items vertivally:
-   `flex-start`: Items align to the top of the container.
-   `flex-end`: Items align to the bottom of the container.
-   `center`: Items align at the vertical center of the container.
-   `baseline`: Items display at the baseline of the container.
-   `stretch`: Items are stretched to fit the container.

## `flex-direction`
defines the direction items :
-   `row`: Items are placed the same as the text direction.
-   `row-reverse`: Items are placed opposite to the text direction.
-   `column`: Items are placed top to bottom.
-   `column-reverse`: Items are placed bottom to top.

## `order`
by default items have a value of 0
```css
#pond {
  display: flex;
}

.yellow {
	order: 1 ;
}
```

## `align-self`
accepts the same values as `align-items` and its valu for the specific item



## `flex-wrap`
-   `nowrap`: Every item is fit to a single line.
-   `wrap`: Items wrap around to additional lines.
-   `wrap-reverse`: Items wrap around to additional lines in reverse.


## `flex-flow`
combines `flex-direction` and `flex-wrap`

> `flex-flow: row  wrap`

## `align-content`
sets how multiple lines are spaced apart from each other
-   `flex-start`: Lines are packed at the top of the container.
-   `flex-end`: Lines are packed at the bottom of the container.
-   `center`: Lines are packed at the vertical center of the container.
-   `space-between`: Lines display with equal spacing between them.
-   `space-around`: Lines display with equal spacing around them.
-   `stretch`: Lines are stretched to fit the container.














