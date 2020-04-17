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
