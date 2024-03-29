

# Vanilla CSS
- remove import *bootstrap/dist/css/bootstrap.css* from `maint.tsx`
- make a new folder `components>ListGroup` 
- inside that folder make  a new file `ComponentName.css`
for example
```css
.list-group{
    list-style:none;
    padding: 10;
}
```
add the file `ListGroup`
add a new file `index.ts`
```typescript
import ListGroup from "./ListGroup";


export default ListGroup
```

and in `App`  use this notation `import ListGroup from "./components/ListGroup"` because React will be searching `import ListGroup from "./components/ListGroup/index"`  

# CSS Module
It is a file in which all class names are scoped locally, so you cane use the same CSS class name in different files without worrying about name clashes

- the css file name e.g. `ListGroup.module.css` 
- and in a tsx  file `import styles from "./ListGroup.module.css` , so all classes defined in that module will be a property of `styles` object:
	-  access  `styles['propertyName']` if you use the class name `list-group` like this or
	- access `style.listGroup` if you use the class name like this `listGroup`
- 
to use in a file `import styles from './ListGroup.module.css'`
```typescript
 <ul className={styles.listGroup}>

               {items.map( (city, index)=><li
```

if you want o to use more than one class
```typescript
 <ul className={[styles.listGroup, styles.container].join(" ")}>

               {items.map( (city, index)=><li
```

# CSS-in-JS

benefits:
- scoped styles
- all the CSS and JS/TS code in one place
- easier to delete a component
- easier to style based on props/state

Necessary library:
- styled components
- emotion
- polished
- 
we will be use `Styled components`
## `npm i styled-components`


























