[[_ 0 w3school React]]

---
# React Render HTML
React renders HTML to the web page by using a function called `ReactDOM.render()`

`ReactDOM.render(<what>, <where>)`
`what` ==HTML code==
`where` ==HTML element==
`ReactDOM(<p> Hello </p>, document.getElementById('root'));`

In the root directory of your React project there is folder named `public` inside there is an `index.html`.
In this file React render HTML

## The HTML Code
You can make a variable containing HTML code:
```JS
const ele=(
	<div> 
		<p> COś tam  </p>
		<p> Tam coś </p>
	
	</div>
)

ReactDOM.render(ele, document.getElementById('root'))
```

The root node is the HTML element where you want to display the result.
It is like a container for content managed by React.









