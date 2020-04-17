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
