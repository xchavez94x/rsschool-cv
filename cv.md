<!-- Styling -->
<!-- <style>
    .cv {
        width: 100%;
        height: 100px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .cv .cv_image {
        width: 100px; 
        height: 100px; 
        border-radius: 100%;
        margin: auto;
    }

    .heading {
        color: #ff8906;
    }

    .colored-text {
        color: #094067;
        font-size: 16px;
        margin-left: ;
    }
    
    .margined {
        margin-left: 12px;
    }

    .link {
        color: #094067;
    }

    .link:hover {
        color: #ff8906;
    }

</style> -->

<!-- markdown  -->


<img   
    class="cv_image"
    src="./profile_image.jpeg" 
    style="width: 100px; height: 100px; border-radius: 100%;"
/>


### Name  
Ahmed Saadun 

<hr >


### Contacts 

* <a class="link" href="https://github.com/xchavez94x?tab=repositories" >Github</a>
* <a class="link" href="https://www.linkedin.com/in/ahmed-saadoon-1463aa1b9/" >Linkedin</a>

<hr />

### About me 

My Name is Ahmed, 
Originally i'm from Iraq but i'd lived in Ukraine since 2013. i've started learning Web development in ITStep academy in kharkiv, i've always been passionate about coding, solving problems, tech, and sometimes gaming.


<hr />

### skills 

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

### Code examples

```
const path = require('path');

const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const multer = require('multer');
const graphqlHttp = require('express-graphql');

const graphqlSchema = require('./graphql/schema');
const graphqlResolver = require('./graphql/resolvers');
const auth = require('./middleware/auth');
const { clearImage } = require('./util/file');

const app = express();

const fileStorage = multer.diskStorage({
  destination: (req, file, cb) => {
    cb(null, 'images');
  },
  filename: (req, file, cb) => {
    cb(null, new Date().toISOString() + '-' + file.originalname);
  }
});

const fileFilter = (req, file, cb) => {
  if (
    file.mimetype === 'image/png' ||
    file.mimetype === 'image/jpg' ||
    file.mimetype === 'image/jpeg'
  ) {
    cb(null, true);
  } else {
    cb(null, false);
  }
};

// app.use(bodyParser.urlencoded()); // x-www-form-urlencoded <form>
app.use(bodyParser.json()); // application/json
app.use(
  multer({ storage: fileStorage, fileFilter: fileFilter }).single('image')
);
app.use('/images', express.static(path.join(__dirname, 'images')));

app.use((req, res, next) => {
  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader(
    'Access-Control-Allow-Methods',
    'OPTIONS, GET, POST, PUT, PATCH, DELETE'
  );
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type, Authorization');
  if (req.method === 'OPTIONS') {
    return res.sendStatus(200);
  }
  next();
});

app.use(auth);

app.put('/post-image', (req, res, next) => {
  if (!req.isAuth) {
    throw new Error('Not authenticated!');
  }
  if (!req.file) {
    return res.status(200).json({ message: 'No file provided!' });
  }
  if (req.body.oldPath) {
    clearImage(req.body.oldPath);
  }
  return res
    .status(201)
    .json({ message: 'File stored.', filePath: req.file.path });
});

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
  .connect(
    'mongodb+srv://maximilian:9u4biljMQc4jjqbe@cluster0-ntrwp.mongodb.net/messages?retryWrites=true'
  )
  .then(result => {
    app.listen(8080);
  })
  .catch(err => console.log(err));




```

