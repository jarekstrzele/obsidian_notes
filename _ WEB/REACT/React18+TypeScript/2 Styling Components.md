

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
- and in a tsx  file `import style from "./ListGroup.module.css` , soe every classes defined in that module will be a property of `style` object 





# CSS-in-JS





















