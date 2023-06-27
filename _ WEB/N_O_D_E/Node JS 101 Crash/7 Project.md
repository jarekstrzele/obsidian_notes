NASA exoplanet archive *Kepler* telescope:
https://exoplanetarchive.ipac.caltech.edu/docs/data.html

KOI table (cumulative list):
https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=cumulative
1. download table as CSV format
2.`mkdir planets-project` and add the file `.csv` to that folder (name the file `kepler_data.csv`)
3. `npm init -yes`
4. `npm install csv-parse`
5. a new file `index.js`
`const { parse } = require('csv-parse') ;`

*CSV parser* implements the `nodejs` *stream API*:

### streams
#node/stream 
- in Node ==all streams== are implemented using the event emitter
- it is a very efficient way to process large data 

#node/buffer 
*buffer* - it is an object that node uses to represent a collection of bytes

![[pipe_node.excalidraw | 700]]

```node
const { parse } = require('csv-parse') ; // parse will be a function

// parse() - returns an event emitter that deals with streams of data

// coming in from the file

// parse() - it knows only streams

const fs = require('fs') ;

  

const results = [] ;

fs.createReadStream('kepler_data.csv')
.pipe(parse({
	comment: '#',
	columns: true, //each rows as a JS object with key-value pairs
	}))
.on('data', (data) => {
	results.push(data) ;
})
.on('error', (err) => {
	console.log(err) ;
})
	.on('end', () => {
console.log(results) ;
console.log('done') ;
});

--- output
[ ...
	{
    kepid: '3832474',
    kepoi_name: 'K00806.03',
    kepler_name: 'Kepler-30 b',
    koi_disposition: 'CONFIRMED',
    koi_pdisposition: 'CANDIDATE',
    koi_score: '',
    ...
    },
```










