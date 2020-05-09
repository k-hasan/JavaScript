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

# redis server (data save)
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
#### redis.js (db conncetion)
```composer log
const redis = require('redis');
const bluebird = require('bluebird');

const client = redis.createClient();
bluebird.promisifyAll(client);

module.exports = client;
```
#### package.json
```composer log
bluebird
```
--------------------

# postgres server (data save)
#### index.js
```composer log
const express = require('express');
const app = express();
const postgres = require('./server/postgres');
const bodyParser = require('body-parser');

app.use(bodyParser.json());


app.post('/task', (req, res) => {
    
    if(req.body.task){
        postgres.Task.create({
            description : req.body.task
        })
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
    postgres.Task.findAll()
    .then(d=>{
        res.json({
            data : d
        })
    }).catch(()=>{
        console.error('error');
    })
})


app.listen(5000);
```

#### postgres.js (db conncetion)

```composer log
const Sequelize = require('sequelize');

//database connection
const database = new Sequelize('mydb', 'myuser', 'mypass', {
    host: 'localhost',
    dialect: 'postgres'
});


//Check databaes connection
database.authenticate()
    .then(()=>{
        console.log('databae connection ok');
    }).catch(e=>{
        console.log('databae connection failed');
    });

// table create
const Task = database.define('task', {
    description: Sequelize.STRING
});

//update schema
database.sync()
    .then(e=>{
        console.log('database sync');
    }).catch(e=>{
        console.log('database sync failed');
    });

module.exports = {
    database,
    Task
};    
```

#### package.json

```composer log
pg, pg-hstore, sequelize
```

# mongo db (data save)
#### index.js
```composer log
const express = require('express');
const app = express();
const Task = require('./server/mongo');
const bodyParser = require('body-parser');

app.use(bodyParser.json());


app.post('/task', (req, res) => {
    let MyName = new Task({ name:req.body.task});
    MyName.save()
        .then(e=>{
            res.json({
                message: 'added'
            });
        }).catch(e=>{
            res.json({
                error : true,
                message: 'not added'
            }).status(500);
        });     
})

app.get('/task', (req, res)=>{
    Task.find({})
    .then(d=>{
        res.json({
            data : d
        })
    }).catch(()=>{
        console.error('error');
    })
})


app.listen(5000);
```

#### mongo.js (db conncetion)
```composer log
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/nodedb', { useNewUrlParser: true, useUnifiedTopology: true });

mongoose.connection.on('error', e=>{
    console.log(e);
});


mongoose.connection.on('open', e=>{
    console.log('connected');
});

// schema
const TaskSchema = new mongoose.Schema({
    name : String
});

// model
const Task = mongoose.model('Task', TaskSchema);

module.exports = Task;
```

#### package.json

```composer log
mongoose
```