Our Funda is very simple. Just create a simple nodeJs app and dockerize it docker hub😘 ...

Step 0: create a folder and create a package.json file. and copy these code

```
{
  "name": "nodejs-image-demo",
  "version": "1.0.0",
  "description": "nodejs image demo",
  "author": "Nisharga Kabir",
  "license": "MIT",
  "main": "app.js",
  "keywords": [
    "nodejs",
    "bootstrap",
    "express"
  ],
  "dependencies": {
    "express": "^4.16.4"
  }
}
```

then do this command

```
npm install
```

This is nothing... just npm init and and doing some answers we can easily make this. but for fast going we ignore this process.

Please make sure you have installed node js and docker on your PC. (you will find lots of videos on YouTube to install docker and nodejs)

Let's Start the Game 😍😍😍

## Step 1: create **app.js** on root and peast this code

```
const express = require("express");
const app = express();
const router = express.Router();


const path = __dirname + "/views/";
const port = 8080;


router.use(function (req, res, next) {
  console.log("/" + req.method);
  next();
});


router.get("/", function (req, res) {
  res.sendFile(path + "index.html");
});


router.get("/sharks", function (req, res) {
  res.sendFile(path + "sharks.html");
});


app.use(express.static(path));
app.use("/", router);


app.listen(port, function () {
  console.log("Example app listening on port 8080!");
});
```

This code says nothing. First, we do a basic setup of express.
Then we got pathName and port for future use. \_ \_ dirname is the absolute path of a file.
Next, we use console.log to see what request we are doing.

Using res.sendFile we say / will be the index.html route
And /sharks will be sharks.html route

Finally specifically said path and app. use router

## Step 2: create two file **views/index.html** and **views/sharks.html**

(make sure to create views folder)

**index.html**

```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>About Sharks</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
    <link href="css/styles.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css?family=Merriweather:400,700" rel="stylesheet" type="text/css">
</head>


<body>
    <nav class="navbar navbar-dark bg-dark navbar-static-top navbar-expand-md">
        <div class="container">
            <button type="button" class="navbar-toggler collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false"> <span class="sr-only">Toggle navigation</span>
            </button> <a class="navbar-brand" href="#">Everything Sharks</a>
            <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
                <ul class="nav navbar-nav mr-auto">
                    <li class="active nav-item"><a href="/" class="nav-link">Home</a>
                    </li>
                    <li class="nav-item"><a href="/sharks" class="nav-link">Sharks</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    <div class="jumbotron">
        <div class="container">
            <h1>Want to Learn About Sharks?</h1>
            <p>Are you ready to learn about sharks?</p>
            <br>
            <p><a class="btn btn-primary btn-lg" href="/sharks" role="button">Get Shark Info Now</a>
            </p>
        </div>
    </div>
    <div class="container">
        <div class="row">
            <div class="col-lg-6">
                <h3>Not all sharks are alike</h3>
                <p>Though some are dangerous, sharks generally do not attack humans. Out of the 500 species known to researchers, only 30 have been known to attack humans.
                </p>
            </div>
            <div class="col-lg-6">
                <h3>Sharks are ancient</h3>
                <p>There is evidence to suggest that sharks lived up to 400 million years ago.
                </p>
            </div>
        </div>
    </div>
</body>


</html>
```

**sharks.html**

```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>About Sharks</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
    <link href="css/styles.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css?family=Merriweather:400,700" rel="stylesheet" type="text/css">
</head>
<nav class="navbar navbar-dark bg-dark navbar-static-top navbar-expand-md">
    <div class="container">
        <button type="button" class="navbar-toggler collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false"> <span class="sr-only">Toggle navigation</span>
        </button> <a class="navbar-brand" href="/">Everything Sharks</a>
        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
            <ul class="nav navbar-nav mr-auto">
                <li class="nav-item"><a href="/" class="nav-link">Home</a>
                </li>
                <li class="active nav-item"><a hreaf="/sharks" class="nav-link">Sharks</a>
                </li>
            </ul>
        </div>
    </div>
</nav>
<div class="jumbotron text-center">
    <h1>Shark Info</h1>
</div>
<div class="container">
    <div class="row">
        <div class="col-lg-6">
            <p>
                <div class="caption">Some sharks are known to be dangerous to humans, though many more are not. The sawshark, for example, is not considered a threat to humans.
                </div>
                <img src="https://assets.digitalocean.com/articles/docker_node_image/sawshark.jpg" alt="Sawshark">
            </p>
        </div>
        <div class="col-lg-6">
            <p>
                <div class="caption">Other sharks are known to be friendly and welcoming!</div>
                <img src="https://assets.digitalocean.com/articles/docker_node_image/sammy.png" alt="Sammy the Shark">
            </p>
        </div>
    </div>
</div>
</html>
```

Finally **views/css/style.css**

```
.navbar {
    margin-bottom: 0;
}


body {
    background: #020A1B;
    color: #ffffff;
    font-family: 'Merriweather', sans-serif;
}


h1,
h2 {
    font-weight: bold;
}


p {
    font-size: 16px;
    color: #ffffff;
}


.jumbotron {
    background: #0048CD;
    color: white;
    text-align: center;
}


.jumbotron p {
    color: white;
    font-size: 26px;
}


.btn-primary {
    color: #fff;
    text-color: #000000;
    border-color: white;
    margin-bottom: 5px;
}


img,
video,
audio {
    margin-top: 20px;
    max-width: 80%;
}


div.caption: {
    float: left;
    clear: both;
}
```

Now do this command

`node app.js`

This command will start the server and you will start your node app 🙂
And visit this URL `http://localhost:8080/` you will see your app running.

I am not describing code here. If you are here to learn node-docker I believe you already know HTML,CSS, and Bootstrap 😎😎😎

## Step 3: DockerFile create

Create `Dockerfile` on root and peast this code

```
FROM node:16-alpine


WORKDIR /app


COPY . .


RUN npm install


EXPOSE 3000


CMD [ "node", "app.js" ]
```

we just say brother. take version 16 (alphine lite version) when you create container inside that app folder our app code will store. copy everything. this install all dependency and finally run it 3000 port with node command 😎

`.dockerignore` create on root

node_modules;
npm - debug.log;
Dockerfile.dockerignore;

this is just because we don't want node_modules folder and others stuff. 😎

## Step 4: Build And Run

open docker app first then

`docker build -t your_dockerhub_username/nodejs-image-demo .`

I am doing here

`docker build -t nisharga/nodeapp .`

We are doing this command. -t means tagname we do it blank but if you wants you can set 🙂

Lets check image created or not by this command

`docker images`

REPOSITORY TAG IMAGE ID CREATED SIZE

We see more about these……. Repo is name. Tag is version id is specific thing. Created is time and size is size

NOW ITS TIME TO BUILD AND RUN 😀

docker build -t nkapp . && docker run -p 1200:8080 nkapp

Now just do these command, -t means tagName -p means port.
-p 1200:8080 means our app is running on port 8080 and we are now running our docker app in 1200 port override 8080.

`http://localhost:1200/` Visit these URL you will see live app from docker build file.

## Step 5: Push the code to docker hub

First register in hub.docker then do these command

`docker login -u DOCKER_NAME  `

Then write password and login 🙂

Now Docker image Push to hubDocker

`docker build -t nisharga/nkapp2:latest .`

`docker push nisharga/nkapp2:latest`

I am building twice to remove confusion. I believe you are already familiar with GitHub. so you already know

githubUserName/RepoName/branchName

here 100% same to same to same thing. BranchName called here tagName. Repo is using appName. The username is used here dockerUser.

Now visit Docker Hub to see your code on docker. Now you can share with dockerize image with anyone, does not matter what device he is using he can easily run it with docker app 😎😎😎😎😎😎
