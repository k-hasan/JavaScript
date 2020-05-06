# Express Install
1. install node
2. install npm or yarn
3. yarn init (create package.json)
4. yarn add express

# bare bone server create
```composer log
const express = require('express');
const app = express();

app.get('/',(req, res)=>{
 res.end('Hello khayrul');
});

app.listen(5000);
```

# nodemon
```composer log
It is need to be install as globally for development environment.

*** you can run server nodemon instead of node ***
```
#Post request with middleware 
```composer log
1. install body-parser middleware 
2. By module.use use for middlewate
Exp:
=====================================
const express = require('express');
const app = express();
const bodyParser = require('body-parser');

app.use(bodyParser.json());

app.get('/',(req, res)=>{
 res.end('Hello khayrul hasan');
});


app.post('/me', (req, res)=>{
  let message = {
   "time" : Date.now(),
   "name" : `Hello ${req.body.name}`
  }
  res.json(message);
});

app.listen(5000);



POSTMAN
===================
{
   "name":"khayrul"
}
```
