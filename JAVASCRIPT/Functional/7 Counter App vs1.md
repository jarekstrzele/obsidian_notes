[[7 - First Functional App From Scratch (Simple Counter)]]


----
==pure function rules==
1. have input parameters
2. no statefule values
3. return based on input
4. no side effects

----

index.js
```javascript
import h from 'hyperscript';
import hh from 'hyperscript-helpers';

const { div, button } = hh(h);
const initModel = 0;

function view(model){
  return div([
    div({className: 'mv2'}, `Count: ${model}`),
    button({className: 'pv1 pv2 mr3', onclick: () => console.log('+ clicked')},'+'),
    button({className: 'pv1 pv2', onclick: () => console.log('- clicked')},'-')
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

const rootNode = document.getElementById('app');

// this has side effect into DOM
rootNode.appendChild(view(update('minus', initModel)));
```

to start project: `npm start`
in package.json is an instruction 
```json

 "scripts": {
    "start": "webpack-dev-server --open"
  },
```

[[7 Counter App vs2]]

[[7 Counter App vs3 - with Virtual DOM]]







