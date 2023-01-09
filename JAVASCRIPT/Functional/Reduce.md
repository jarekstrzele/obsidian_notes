[[0- Intro functional programming (beginner udemy)]]
[[Modify arrays in immutable way]]

---

# Reduce
#javascript/reduce
```js
const numbers = [1,2,3];  
function sum(x,y){  
      return x+y;  
}
const total = numbers.reduce(sum)
```


```js
const grades = [60, 55, 80, 90, 99, 92, 75,72]
function sum(acc, grade){
	return acc+grade;
};

const total = grades.reduce(sum);
console.log(total, total/grades.length)


// reduce(function, firstParameter)
// our first acc will be an empty object {}
const letterGradeCount = grades.reduce(groupByGrade, {})

//unpacked accumulater:
{a=0,b=0,c=0,d=0,f=0} = acc

// at the begining acc={}
function groupByGrade(acc, grade){
	if(grade>=90){
		return {...acc, a: a + 1} 
		else if(grade >0 80)

	
	```

task:
```js
const reviews = [4.5, 4.0, 5.0, 2.0, 1.0, 5.0, 3.0, 4.0, 1.0, 5.0, 4.5, 3.0, 2.5, 2.0];

// 1. Using the reduce function, create an object that
// has properties for each review value, where the value
// of the property is the number of reviews with that score.
// for example, the answer should be shaped like this:
// { 4.5: 1, 4.0: 2 ...}

const countGroupedByReview = reviews.reduce(groupBy, {});

function groupBy (acc, review){
  const count = acc[review] || 0;
  return {...acc, [review]: count + 1}
}

console.log(countGroupedByReview);


```
