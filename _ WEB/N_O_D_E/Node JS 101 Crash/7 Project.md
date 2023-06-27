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
- it is a very efficant way to process large data 
















