
Add a new folder in the components folder `Chart`.

Write/Declare `Chart.jsx` (not only for months)
```jsx
import React from 'react' ;
import ChartBar from './ChartBar' ;

const Chart = props => {
    return (
    <div >
      {props.dataPOints.map(dataPoint => <ChartBar 
                                       key={key.label}
                                       value={dataPoint.value}
                                       maxValue={null}
                                       label={dataPoint.label}
                                       
      }
    </div>
    ) 
    
}

export default Chart ;
```

`ChartBar.jsx`
```jsx
import React from 'react' ;


const ChartBar = props => {
  // How much we fill the bar depends on the data we're receiving (value)
  let barFillHeight = '0%' ;
  
  if (props.max>0){
    Math.round((props.value / props.maxValue) * 100 ) + '%' ;
  }
  
  return (<div>
           <div>
            <div style={{height: barFillHeight}}> </div>
           </div>
          <div> {props.label} </div> {/* label */}  
  
  
          </div>)
    
}

export default ChartBar ;


```


To use the Chart component and pass in the data points we will create a new component in Expenses forlde:
`ExpensesChart.jsx`
```jsx
import React from 'react' ;
import Chart from '../Chart/Chart' ;
const ExpensesChart = props => {
  
  const chartDataPoints = [
    {label: 'Jan', value:0},
    {label: 'Feb', value:0},
    {label: 'Mar', value:0},
    {label: 'Apr', value:0},
    {label: 'May', value:0},
    {label: 'Jun', value:0},
    {label: 'Jul', value:0},
    {label: 'Aug', value:0},
    {label: 'Sep', value:0},
    {label: 'Oct', value:0},
    {label: 'Nov', value:0},
    {label: 'Dec', value:0},
  ]

  for (const expense of props.expenses){
    const expenseMonth = expense.data.getMonth() ; // index 0 -> January
    chartDataPoints[expenseMonth].value += expense.amount ;
  }
  
  return <Chart dataPoints={chartDataPoints} /> 
}

export default ExpensesChart ;

```




To use this Chart Component go to the main file `App.jsx`/  `Expenses.jsx`











