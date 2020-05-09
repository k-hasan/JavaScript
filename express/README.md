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

#### Create module and use main js 

```javascript
file : src/route.js
-------------------------------------
module.exports = function (app) {
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
}

index.js
--------------------------------
const express = require('express');
const app = express();
const bodyParser = require('body-parser');
const route = require('./src/route');

app.use(bodyParser.json());

route(app);

app.listen(5000);



************************************** 
    Object নন প্রিমিটিভ টাই call by referance 
    আর যা প্রিমিটিভ তা call by value  
**************************************
```

# Static file serve and set middleware on specific routes 
```composer log
    const path = reqire('path');
    app.get('/public/index.html', (req, res)=>{
        res.sendFile(path.resolve(__dirname, "./public/index.html")); 
    });
or

app.use('/pub', express.static('public'))
```

# custom middle ware create
```composer log
const express = require('express');
const app = express();
const fixToken = 'bangladeshd';

//create middleware 
app.use('/api', (req, res, next)=>{
   let msg = function (m, s){
        return res.json({
            message : m
        }).status(s)
    };

    let token = req.header('token');
    if(!token){
        return msg('unautorized', 401);
    }else {
        if(token === fixToken){

            return next();
        }else{
            return msg('wrong', 401);
        }
    }
});


//Route
app.get('/api', (req, res)=> {
    res.json({
        "message": "hellow khayrul"
    });
})
```

# resis server
#### index.js
```composer log
const express = require('express');
const app = express();
const rc = require('./redis');

const bodyParser = require('body-parser');

app.use(bodyParser.json());


app.post('/task', (req, res) => {
    
    if(req.body.task){
        rc.lpushAsync('my_tasks', req.body.task)
        .then(e=>res.json({message:"data saved!"}));
    }
    else{
        res.json({
            error : true,
            message : "data properly set",
        }).status(404)
    }
})

app.get('/task', (req, res)=>{
    rc.lrangeAsync('my_tasks', 0, -1)
    .then(d=>{
        res.json({
            data : d
        })
    }).then(()=>{
        
        console.error('sfsdfsdfsd');
        
    })
})


app.listen(5000);
```
#### redis.js
```composer log
const redis = require('redis');
const bluebird = require('bluebird');

const client = redis.createClient();
bluebird.promisifyAll(client);

module.exports = client;
```

