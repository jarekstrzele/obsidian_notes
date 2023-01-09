tworzymy projekt
`$ ng new todo-list-udemy`

doinstalowujemy
`$ npm install materialize-css@1.0.0`

dodajemy ` "./node_modules/materialize-css/dist/css/materialize.css"`
do angular.js>"style":[]

potem do "script"
` "./node_modules/materialize-css/dist/js/materialize.js"`

Jest to potrzebne, aby Angular "Widział" _materialize_

(tak samo konfiguruje się np. bootstrap)

z githuba z app.commponent.css
kopiujemy i w klejamy
w naszej aplikacji w analogicznym miejscu

tak samo z html

z _index.html_ kopiujemy link do _materialize_ i wklejamy go w head w index.html aplikacji naszej

w pliku .ts 
`export class AppComponent {}`


URUCHAMIAMY APLIKACJĘ:
`ng serve`


