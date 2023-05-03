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
![[simple_list_app.excalidraw | 500]]


App.css
```css
#goals {
  width: 35rem;
  max-width: 90%;
  margin: 3rem auto;
}

#goal-form {
  width: 30rem;
  max-width: 70%;
  margin: 3rem auto;
  padding: 2rem;
  box-shadow: 0 2px 12px rgba(0,0,0, 0.3);
  border-radius: 10px;
}
```

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



CourseInput.css
```css
.form-control {
  margin: 0.5rem 0;
}

.form-control label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

.form-control input {
  display: block;
  width: 100%;
  border: 1px solid #ccc;
  font: inherit;
  line-height: 1.5rem;
  padding: 0 0.25rem;
}

.form-control input:focus {
  outline: none;
  background: #fad0ec;
  border-color: #8b005d;
}
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



CourseGoalList.css
```css
.goal-list {
  list-style: none;
  margin: 0;
  padding: 0;
}
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


CourseGoalItem
```css
.goal-item {
  margin: 1rem 0;
  background: #8b005d;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  color: white;
  padding: 1rem 2rem;
  cursor: pointer;
}
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







