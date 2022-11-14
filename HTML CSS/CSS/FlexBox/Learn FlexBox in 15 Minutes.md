https://www.youtube.com/watch?v=fYq5PXgSsbE&list=PLZlA0Gpn_vH85jM1TWO6TdCtSr6ruglWn&index=8


# Learn FlexBox in 15 Minutes
#flexbox    #web_dev_simplified #youtube


**LEFT - RIGHT (main axis)**
`justify-content`:
	- start (left)
	- center
	- end (right)
	-  `justify-content: space-between;`
	- `justify-content: space-between;`
but if you switch `flex-direction` to `column`, the property `justify-content` starts to align (top-buttom) and `align-items` from left to right




**TOP - BOTTOM (cross axis)**
`align-items`:
	- strech (by default) (take max place)
	- start (top) (returns previous shape)
	- center
	- end


**SHRINK**
*shrink* kurczyć się
`flex-shrink: 0;` this flex item  will not shrink during the screen resizing

**GROW**
`flex-grow: 1;` this item fulls all the space during the window browser resizing.

`flex-basis: 0;` this override other settings and  this item will startto grow from zero


**ALIGN-SELF**
this rule override other
you can change the place of an item

**ORDER**
`order: 1`


## shortcuts
In the css item:
`flex: [flex-grow] [flex-shrink]  [flex basis]`
or
`fex: [flex-grow]` other will be set automatically





