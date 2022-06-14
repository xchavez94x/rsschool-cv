### Ahmed Saadun   


<hr >


### Contacts 

* <a class="link" href="https://github.com/xchavez94x?tab=repositories" >Github</a>
* <a class="link" href="https://www.linkedin.com/in/ahmed-saadoon-1463aa1b9/" >Linkedin</a>

<hr />

### About me 

My Name is Ahmed, 
Originally i'm from Iraq but i'd lived in Ukraine since 2013. i've started learning Web development in ITStep academy in kharkiv, i've always been passionate about coding, solving problems, tech, and sometimes gaming.


<hr />

### Skills 

* HTML5, 
* CSS3, Sass, Less, Boostrap, 
* Vanilla Javascript 
* MERN stack, Redux, Redux toolkit, Redux Saga, Router 
* Php, Laravel (Some basic skills), Mysql 
* Git, Github 
* Gulp, Grunt
* OOP, Solid 
* Npm, yarn

<hr/>

### Code example

##### indesx.js

```js
const path = require('path');

const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const multer = require('multer');
const graphqlHttp = require('express-graphql');
const cors = require('cors');

const graphqlSchema = require('./graphql/schema');
const graphqlResolver = require('./graphql/resolvers');

const app = express();
const port = process.env.DB_URI || 3000

app.use(bodyParser.json()); 

app.use(
  '/graphql',
  graphqlHttp({
    schema: graphqlSchema,
    rootValue: graphqlResolver,
    graphiql: true,
    formatError(err) {
      if (!err.originalError) {
        return err;
      }
      const data = err.originalError.data;
      const message = err.message || 'An error occurred.';
      const code = err.originalError.code || 500;
      return { message: message, status: code, data: data };
    }
  })
);

app.use((error, req, res, next) => {
  console.log(error);
  const status = error.statusCode || 500;
  const message = error.message;
  const data = error.data;
  res.status(status).json({ message: message, data: data });
});

mongoose
  .connect()
  .then(result => {
    app.listen(port);
  })
  .catch(err => console.log(err));
  ```

#### 
