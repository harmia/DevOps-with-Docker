# 1.1 Getting started
## Submitting the output for docker ps -a is enough to prove this exercise has been done.


juhana.harmanen@G0475 ~ % docker ps -as
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS                          PORTS               NAMES                 SIZE
a47a52b1224d        nginx               "nginx -g 'daemon of…"   About a minute ago   Up About a minute               80/tcp              confident_zhukovsky   2B (virtual 127MB)
2f9cade70dac        nginx               "nginx -g 'daemon of…"   About a minute ago   Exited (0) About a minute ago                       angry_wiles           0B (virtual 127MB)
16d74c698529        nginx               "nginx -g 'daemon of…"   About a minute ago   Exited (0) About a minute ago                       distracted_ellis      0B (virtual 127MB)
juhana.harmanen@G0475 ~ %


# 1.2 Cleanup
## Submit the output for docker ps -a and docker images


juhana.harmanen@G0475 ~ % docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
juhana.harmanen@G0475 ~ % docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
juhana.harmanen@G0475 ~ %


# 1.3 Hello Docker Hub
## Submit the secret message and command(s) given to get it as your answer.


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


# 1.4 Docker is easy
## Submit the secret message and command(s) given as your answer.


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


# 1.5 Docker exec -it
## This time return the command you used to start process and the command(s) you used to fix the ensuing problems.


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


# 1.6 Docker build -t docker-clock
## Return both Dockerfile(s) and the command you used to run the container(s)


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


# 1.7 Docker build -t curler
## Return both Dockerfile(s) and the command you used to run the container(s)


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


# 1.8 Volume bind mount is easy
## Submit your used commands for this exercise.


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
