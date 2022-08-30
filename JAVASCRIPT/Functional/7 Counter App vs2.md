[[7 - First Functional App From Scratch (Simple Counter)]]

[[7 Counter App vs1]]


---
# Counter App vs 2


**PURE**:         initModel, update(), view()
**IMPURE**:   State, Side Effect (DOM)

life of our counter app:
1. initModel =0 -> this is a beginning state=0
2. calling a view funct with the begining state=0
3. view create html and send it to DOM (side effects)
4. when button are clicked a DOM  calls handler functions we provided in a view function
5. when update function is called with correct msg (which button) and current state of the app
6. so update function return a new state (e.i. = 1)
7. because the app has a new state, the view function should be called
8. and the view function will change the DOM

so a new version of the app
```js
import h from 'hyperscript';
import hh from 'hyperscript-helpers';

const { div, button } = hh(h);
const initModel = 0;

function view(dispatch, model){
  return div([
    div({className: 'mv2'}, `Count: ${model}`),
    button({className: 'pv1 pv2 mr3', onclick: () => dispatch('plus')},'+'),
    button({className: 'pv1 pv2', onclick: () => dispatch('minus')},'-')
  ])
}

function update(msg, model){
  switch(msg){
    case 'plus':
      return model + 1;
    case 'minus':
      return model -1;
    default:
      return model;
  }
}

//impure code
function app(initModel, update, view, node){
  let model = initModel;
  let currentView = view(dispatch, model);
  node.appendChild(currentView);

  function dispatch(msg){
    model = update (msg, model);
    const updatedView = view(dispatch, model);
    node.replaceChild(updatedView, currentView);
    currentView = updatedView;
  }
}

const rootNode = document.getElementById('app');
app(initModel, update, view, rootNode);
//rootNode.appendChild(view(update('minus', initModel)));
```


but we can change:
- msg 
- use **virtual DOM** - it's a performance library that will sit between the view our app generates and the DOM, because now we change all of our html, but we need to change a small piece of html





