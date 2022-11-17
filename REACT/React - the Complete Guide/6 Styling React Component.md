#react/props  
https://www.youtube.com/watch?v=JpM9hiQTlAk&t=2s

# Some new issues
## `props.children`

> You can use props.children in React in order to access and utilize what you put inside the open and closing tags when you are creating an instance of a component.
> 

App.jsx
```jsx
import './App.css'
import Button from './Button' ;

export default function App() {
  return (
    <div>
      <Button> hej </Button>
      <Button> Hello </Button>
    </div>
  )
}
```

Button.jsx
```jsx
export default function Button(props){
  return (
    <button>{props.children}  </button>
  ) ;
}
```

---
Card.jsx
```jsx
export default function Card(props){

  const cardStyle = {
    width: '200px',
    height:'100px',
    border: '1.5px solid gray',
    borderRadius: '2px',
    padding: '4px',
    margin: '4px'
  }
  
  return (
    <div style={cardStyle}>
      {children}
    
    </div>
  ) ;
}
```

new App.jsx
```jsx
import './App.css'
import Button from './Button' ;
import Card from './Card' ;
export default function App() {
  return (
  <div>
    <Card>
      <Button> hej </Button>
      <Button> Hello </Button>
    </Card>

     <Card>
      Lorem ipsumLorem ipsumLorem ipsumLorem ipsum
       Lorem ipsumLorem ipsumLorem ipsumLorem ipsumLorem ipsum
       Lorem ipsumLorem ipsumLorem ipsumLorem ipsum
    </Card>
   </div> 
  )
}
```


----
# Simple List App
simple stucture:





App.jsx
```jsx
import React, { useState } from 'react';
import CourseGoalList from './components/CourseGoals/CourseGoalList/CourseGoalList';
import CourseInput from './components/CourseGoals/CourseInput/CourseInput';
import './App.css';

const App = () => {
  const [courseGoals, setCourseGoals] = useState([
    { text: 'Do all exercises!', id: 'g1' },
    { text: 'Finish the course!', id: 'g2' }
  ]);

  const addGoalHandler = enteredText => {
    setCourseGoals(prevGoals => {
      const updatedGoals = [...prevGoals];
      updatedGoals.unshift({ text: enteredText, id: Math.random().toString() });
      return updatedGoals;
    });
  };

  const deleteItemHandler = goalId => {
    setCourseGoals(prevGoals => {
      const updatedGoals = prevGoals.filter(goal => goal.id !== goalId);
      return updatedGoals;
    });
  };

  let content = (
    <p style={{ textAlign: 'center' }}>No goals found. Maybe add one?</p>
  );

  if (courseGoals.length > 0) {
    content = (
      <CourseGoalList items={courseGoals} onDeleteItem={deleteItemHandler} />
    );
  }

  return (
    <div>
     
      <section id="goal-form">
        <CourseInput onAddGoal={addGoalHandler} />
      </section>
      <section id="goals">
        {content}
        {/* {courseGoals.length > 0 && (
          <CourseGoalList
            items={courseGoals}
            onDeleteItem={deleteItemHandler}
          />
        ) // <p style={{ textAlign: 'center' }}>No goals found. Maybe add one?</p>
        } */}
      </section>
    </div>
  );
};
```

CourseInput.jsx
```jsx
import React, { useState } from 'react';
import Button from '../../UI/Button/Button';
import './CourseInput.css';

const CourseInput = props => {
  const [enteredValue, setEnteredValue] = useState('');

  const goalInputChangeHandler = event => {
    setEnteredValue(event.target.value);
  };

  const formSubmitHandler = event => {
    event.preventDefault();
    props.onAddGoal(enteredValue);
  };

  return (
    <form onSubmit={formSubmitHandler}>
      <div className="form-control">
        <label>Course Goal</label>
        <input type="text" onChange={goalInputChangeHandler} />
      </div>
      <Button type="submit">Add Goal</Button>
    </form>
  );
};

export default CourseInput;

```






CourseGoalList.jsx
```jsx
import React from 'react';

import CourseGoalItem from '../CourseGoalItem/CourseGoalItem';
import './CourseGoalList.css';

const CourseGoalList = props => {
  return (
    <ul className="goal-list">
      {props.items.map(goal => (
        <CourseGoalItem
          key={goal.id}
          id={goal.id}
          onDelete={props.onDeleteItem}
        >
          {goal.text}
        </CourseGoalItem>
      ))}
    </ul>
  );
};

export default CourseGoalList;

```


CourseGoalItem.jsx
```jsx
import React from 'react';
import './CourseGoalItem.css';

const CourseGoalItem = props => {
  // const [deleteText, setDeleteText] = useState('');
  const deleteHandler = () => {
    // setDeleteText('(Deleted!)');
    props.onDelete(props.id);
  };

  return (
    <li className="goal-item" onClick={deleteHandler}>
      {props.children}
    </li>
  );
};

export default CourseGoalItem;

```







