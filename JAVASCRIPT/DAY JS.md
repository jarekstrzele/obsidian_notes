#javascript  #dayjs 


------
# Using Daj.js in React
https://www.youtube.com/watch?v=vxBwVEhIzdA

https://day.js.org/
docs > plugins > relative time


`import dayjs from "dayjs"`

```jsx
import relativeTime from "dayjs/plugin/relativeTime" ;


dayjs.extend(relativeTime) ;
const commentTIme = dayjs(createdDate).fromNow() ; //createdDate comes from props

```


