# HelloDocker
## What is Docker?
Docker is the de facto standard for building, shipping and running applications in a consistent manner. That's why most companies use it and are looking for developers with Docker skills.

## Install Docker
Go to docker website, and download `Docker.dmg`

Create a new folder
```bash
$ mkdir hello-docker
```
Create a `.js` file
```bash
$ code app.js
```
Type `console.log("Hello, Docker!");` and run
```
$ node app.js
```
Then, we are going to create a docker file
```bash
$ code Dockerfile #without extensions
```
Type the following code
```docker
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js
```
Build docker container
```bash
$ docker build -t hello-docker .
# or docker build -t hello-docker . --platform linux/amd64
# second docker means the folder name
# . means the dockerfile is in the current folder
```
View the image
```bash
$ docker image ls
```
Run without call `node app.js`
```bash
docker run hello-docker
```
Try if it works. Go to [Play with Docker](https://labs.play-with-docker.com). There are only linux and docker so we can't run `node` or `python` here.

## Login Docker Hub via VSCode
To use the access token from your Docker CLI client:
1. Run `docker login -u [username]`
2. At the password prompt, enter the personal access token.

Push to the docker remote
```bash
# rename tag
$ docker tag hello-docker huixinyang/hello-docker:latest
# push to the remote
$ docker push huixinyang/hello-docker:latest
```
You can view the repository via Docker Hub

Back to Play with Docker
```bash
$ docker pull huixinyang/hello-docker
```

Check if the image exists
```bash
$ docker image ls
```

Run the program without calling node
```bash
$ docker run  huixinyang/hello-docker
```
## Work with github
### Push an existing repository from the command line
```bash
$ git init
$ git remote add origin https://github.com/HUIXIN-TW/HelloDocker.git
$ git branch -M master
$ git add .
$ git commit -m "init"
$ git push -u origin master
```

### Create a new repository on the command line
```bash
$ echo "# HelloDocker" >> README.md
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git branch -M master
$ git remote add origin https://github.com/HUIXIN-TW/HelloDocker.git
$ git push -u origin master
```