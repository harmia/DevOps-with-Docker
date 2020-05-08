# 1.1 Getting started
## Submitting the output for docker ps -a is enough to prove this exercise has been done.


```
juhana.harmanen@G0475 ~ % docker ps -as
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS                          PORTS               NAMES                 SIZE
a47a52b1224d        nginx               "nginx -g 'daemon of…"   About a minute ago   Up About a minute               80/tcp              confident_zhukovsky   2B (virtual 127MB)
2f9cade70dac        nginx               "nginx -g 'daemon of…"   About a minute ago   Exited (0) About a minute ago                       angry_wiles           0B (virtual 127MB)
16d74c698529        nginx               "nginx -g 'daemon of…"   About a minute ago   Exited (0) About a minute ago                       distracted_ellis      0B (virtual 127MB)
juhana.harmanen@G0475 ~ %
```


# 1.2 Cleanup
## Submit the output for docker ps -a and docker images


```
juhana.harmanen@G0475 ~ % docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
juhana.harmanen@G0475 ~ % docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
juhana.harmanen@G0475 ~ %
```


# 1.3 Hello Docker Hub
## Submit the secret message and command(s) given to get it as your answer.


```
juhana.harmanen@G0475 ~ % docker run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete
5e2195587d10: Pull complete
6f595b2fc66d: Pull complete
165f32bf4e94: Pull complete
67c4f504c224: Pull complete
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"

juhana.harmanen@G0475 ~ %
```


# 1.4 Docker is easy
## Submit the secret message and command(s) given as your answer.


```
juhana.harmanen@G0475 ~ % docker run -d devopsdockeruh/exec_bash_exercise
Unable to find image 'devopsdockeruh/exec_bash_exercise:latest' locally
latest: Pulling from devopsdockeruh/exec_bash_exercise
741437d97401: Already exists
34d8874714d7: Already exists
0a108aa26679: Already exists
7f0334c36886: Already exists
65c95cb8b3be: Already exists
a36b708560f8: Already exists
4090f912e6c7: Already exists
ce5fe2607c2e: Already exists
9400f5f657d6: Already exists
c4919883f7fa: Already exists
Digest: sha256:c463832132d1fb0b8b3b60348a6fc36fda7512a4ef2d1050e8bea7b6a6d7a2f3
Status: Downloaded newer image for devopsdockeruh/exec_bash_exercise:latest
787c74327243ad266b8c33ab49216b81af02e210dbfb8fb8b0269d921db94301
juhana.harmanen@G0475 ~ % docker exec -it 787c74327243 bash
root@787c74327243:/usr/app# tail -f ./logs.txt
Thu, 16 Apr 2020 20:14:05 GMT
Secret message is:
"Docker is easy"
Thu, 16 Apr 2020 20:14:11 GMT
Thu, 16 Apr 2020 20:14:14 GMT
Thu, 16 Apr 2020 20:14:17 GMT
Thu, 16 Apr 2020 20:14:20 GMT
Secret message is:
"Docker is easy"
Thu, 16 Apr 2020 20:14:26 GMT
Thu, 16 Apr 2020 20:14:29 GMT
Thu, 16 Apr 2020 20:14:32 GMT
Thu, 16 Apr 2020 20:14:35 GMT
^C
root@787c74327243:/usr/app# exit
exit
juhana.harmanen@G0475 ~ %
```


# 1.5 Docker exec -it
## This time return the command you used to start process and the command(s) you used to fix the ensuing problems.


```
juhana.harmanen@G0475 ~ % docker exec -it 787c74327243 sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
juhana.harmanen@G0475 ~ %
```


# 1.6 Docker build -t docker-clock
## Return both Dockerfile(s) and the command you used to run the container(s)


```
juhana.harmanen@G0475 1.6 % docker build -t docker-clock .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM devopsdockeruh/overwrite_cmd_exercise
 ---> 3d2b622b1849
Step 2/2 : CMD ["-c"]
 ---> Running in 323e6c68c0fb
Removing intermediate container 323e6c68c0fb
 ---> 185c1536004d
Successfully built 185c1536004d
Successfully tagged docker-clock:latest
juhana.harmanen@G0475 1.6 % docker run docker-clock       
1
2
3
4
5
juhana.harmanen@G0475 1.6 %
```


# 1.7 Docker build -t curler
## Return both Dockerfile(s) and the command you used to run the container(s)


```
juhana.harmanen@G0475 1.7 % docker build -t curler .
Sending build context to Docker daemon  3.072kB
Step 1/4 : FROM ubuntu
 ---> 4e5021d210f6
Step 2/4 : RUN apt-get update && apt-get install -y curl
 ---> Running in e201a18d9598
...
Successfully built 9f9f5dbf69aa
Successfully tagged curler:latest
juhana.harmanen@G0475 1.7 % docker run -it curler   
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
juhana.harmanen@G0475 1.7 %
```


# 1.8 Volume bind mount is easy
## Submit your used commands for this exercise.


```
juhana.harmanen@G0475 1.8 % docker run -v $(pwd)/logs.txt:/usr/app/logs.txt devopsdockeruh/first_volume_exercise
(node:1) ExperimentalWarning: The fs.promises API is experimental
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
^CClosing file
juhana.harmanen@G0475 1.8 %
```


# 1.9 Docker run -p 80:80
## Submit your used commands for this exercise.


```
juhana.harmanen@G0475 DevOps-with-Docker % docker run -p 80:80 devopsdockeruh/ports_exercise
Unable to find image 'devopsdockeruh/ports_exercise:latest' locally
latest: Pulling from devopsdockeruh/ports_exercise
cd784148e348: Pull complete
9abca35fefbf: Pull complete
7fc670963d22: Pull complete
893040f9bc16: Pull complete
b0ae6401e570: Pull complete
Digest: sha256:2ff93dd0c744aee7a8f00bc9558d09fd6279493da0d01769fe600f78fb4593f2
Status: Downloaded newer image for devopsdockeruh/ports_exercise:latest

> ports_exercise@1.0.0 start /usr/app
> node index.js

Listening on port 80, this means inside of the container. Use -p to map the port to a port of your local machine.
^C%                                                                                                                             juhana.harmanen@G0475 DevOps-with-Docker %
```


# 1.10 Frontend
## Submit the Dockerfile.


```
juhana.harmanen@G0475 1.10 % docker build -t frontend-1.10 .    
Sending build context to Docker daemon  585.7kB
Step 1/12 : FROM node:alpine
 ---> bcfeabd22749
Step 2/12 : WORKDIR /usr/app
 ---> Using cache
 ---> f2f7b365d628
Step 3/12 : COPY ./package*.json ./
 ---> Using cache
 ---> b8749a9c85e0
Step 4/12 : RUN npm install
 ---> Using cache
 ---> 09f84f899d7d
Step 5/12 : COPY ./src ./src
 ---> Using cache
 ---> b33437e2ead5
Step 6/12 : COPY ./util ./util
 ---> Using cache
 ---> f06245100a2c
Step 7/12 : COPY ./config.js ./config.js
 ---> Using cache
 ---> 7e32da42dc96
Step 8/12 : COPY ./webpack.config.js ./webpack.config.js
 ---> Using cache
 ---> 4f7ce4576575
Step 9/12 : RUN npm run build
 ---> Using cache
 ---> e99b0c911c4c
Step 10/12 : RUN npm install -g serve
 ---> Using cache
 ---> ebb01dab5670
Step 11/12 : CMD serve -s -l 5000 dist
 ---> Using cache
 ---> 1a798bfd046a
Step 12/12 : EXPOSE 5000
 ---> Using cache
 ---> f01dda717a7f
Successfully built f01dda717a7f
Successfully tagged frontend-1.10:latest
juhana.harmanen@G0475 1.10 % docker run -p 5000:5000 frontend-1.10
INFO: Accepting connections at http://localhost:5000
^C
INFO: Gracefully shutting down. Please wait...
juhana.harmanen@G0475 1.10 %
```


# 1.11 Backend
## Submit the Dockerfile and the command used.


```
juhana.harmanen@G0475 1.11 % docker build -t backend-1.11 .                         
Sending build context to Docker daemon  196.6kB
Step 1/10 : FROM node:alpine
 ---> bcfeabd22749
Step 2/10 : WORKDIR /usr/app
 ---> Using cache
 ---> f2f7b365d628
Step 3/10 : COPY ./package*.json ./
 ---> Using cache
 ---> 92edadd1e450
Step 4/10 : RUN npm install
 ---> Using cache
 ---> cf9ecf53155e
Step 5/10 : COPY ./server ./server
 ---> Using cache
 ---> 061120e0579a
Step 6/10 : COPY ./config.js ./config.js
 ---> Using cache
 ---> 1441dde84098
Step 7/10 : COPY ./index.js ./index.js
 ---> Using cache
 ---> bdf2fb487b68
Step 8/10 : VOLUME ./logs.txt
 ---> Using cache
 ---> c5ffd4985ac3
Step 9/10 : CMD npm start
 ---> Using cache
 ---> d5e4af4e5992
Step 10/10 : EXPOSE 8000
 ---> Using cache
 ---> ffb24cc1da08
Successfully built ffb24cc1da08
Successfully tagged backend-1.11:latest
juhana.harmanen@G0475 1.11 % docker run -p 8000:8000 -v $(pwd)/logs.txt:/usr/app/logs.txt backend-1.11

> backend-example-docker@1.0.0 start /usr/app
> cross-env NODE_ENV=production node index.js

Browserslist: caniuse-lite is outdated. Please run next command `npm update caniuse-lite browserslist`
Started on port 8000
^C%                                                                                                                             juhana.harmanen@G0475 1.11 %
```


# 1.12 Frontend + Backend
## Submit the edited Dockerfiles and commands used to run.

```
juhana.harmanen@G0475 frontend % docker build -t frontend-1.12 .                             
Sending build context to Docker daemon  585.2kB
Step 1/13 : FROM node:alpine
 ---> bcfeabd22749
Step 2/13 : WORKDIR /usr/app
 ---> Using cache
 ---> f2f7b365d628
Step 3/13 : COPY ./package*.json ./
 ---> Using cache
 ---> b8749a9c85e0
Step 4/13 : RUN npm install
 ---> Using cache
 ---> 09f84f899d7d
Step 5/13 : COPY ./src ./src
 ---> Using cache
 ---> b33437e2ead5
Step 6/13 : COPY ./util ./util
 ---> Using cache
 ---> f06245100a2c
Step 7/13 : COPY ./config.js ./config.js
 ---> Using cache
 ---> 7e32da42dc96
Step 8/13 : COPY ./webpack.config.js ./webpack.config.js
 ---> Using cache
 ---> 4f7ce4576575
Step 9/13 : ENV API_URL=http://localhost:8000
 ---> Using cache
 ---> 91674903d976
Step 10/13 : RUN npm run build
 ---> Using cache
 ---> c9bf6a8add88
Step 11/13 : RUN npm install -g serve
 ---> Using cache
 ---> bca1e5fc9038
Step 12/13 : CMD serve -s -l 5000 dist
 ---> Using cache
 ---> 4674ceb56294
Step 13/13 : EXPOSE 5000
 ---> Using cache
 ---> 715a5ba02709
Successfully built 715a5ba02709
Successfully tagged frontend-1.12:latest
juhana.harmanen@G0475 frontend % docker run -p 5000:5000 frontend-1.12
INFO: Accepting connections at http://localhost:5000
```
```
juhana.harmanen@G0475 backend % docker build -t backend-1.12 .
Sending build context to Docker daemon  196.1kB
Step 1/11 : FROM node:alpine
 ---> bcfeabd22749
Step 2/11 : WORKDIR /usr/app
 ---> Using cache
 ---> f2f7b365d628
Step 3/11 : COPY ./package*.json ./
 ---> Using cache
 ---> 92edadd1e450
Step 4/11 : RUN npm install
 ---> Using cache
 ---> cf9ecf53155e
Step 5/11 : COPY ./server ./server
 ---> Using cache
 ---> 061120e0579a
Step 6/11 : COPY ./config.js ./config.js
 ---> Using cache
 ---> 1441dde84098
Step 7/11 : COPY ./index.js ./index.js
 ---> Using cache
 ---> bdf2fb487b68
Step 8/11 : VOLUME ./logs.txt
 ---> Using cache
 ---> c5ffd4985ac3
Step 9/11 : ENV FRONT_URL=http://localhost:5000
 ---> Using cache
 ---> d1f830b7db4a
Step 10/11 : CMD npm start
 ---> Using cache
 ---> ad900b5ddb5d
Step 11/11 : EXPOSE 8000
 ---> Using cache
 ---> eebd163e5f33
Successfully built eebd163e5f33
Successfully tagged backend-1.12:latest
juhana.harmanen@G0475 backend % docker run -p 8000:8000 -v $(pwd)/logs.txt:/usr/app/logs.txt backend-1.12

> backend-example-docker@1.0.0 start /usr/app
> cross-env NODE_ENV=production node index.js

Browserslist: caniuse-lite is outdated. Please run next command `npm update caniuse-lite browserslist`
Started on port 8000
```
