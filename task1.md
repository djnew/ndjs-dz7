1)
```shell
djnew@HOME_PC:~$ docker pull busybox:latest
latest: Pulling from library/busybox
Digest: sha256:f7ca5a32c10d51aeda3b4d01c61c6061f497893d7f6628b92f822f7117182a57
Status: Downloaded newer image for busybox:latest
docker.io/library/busybox:latest
```
2)
```shell
djnew@HOME_PC:~$ docker run -i -t --rm --name pinger busybox ping -w 7 netology.ru
PING netology.ru (104.22.49.171): 56 data bytes
64 bytes from 104.22.49.171: seq=0 ttl=37 time=37.565 ms
64 bytes from 104.22.49.171: seq=1 ttl=37 time=38.427 ms
64 bytes from 104.22.49.171: seq=2 ttl=37 time=37.597 ms
64 bytes from 104.22.49.171: seq=3 ttl=37 time=37.608 ms
64 bytes from 104.22.49.171: seq=4 ttl=37 time=37.176 ms
64 bytes from 104.22.49.171: seq=5 ttl=37 time=37.470 ms
64 bytes from 104.22.49.171: seq=6 ttl=37 time=37.441 ms

--- netology.ru ping statistics ---
7 packets transmitted, 7 packets received, 0% packet loss
round-trip min/avg/max = 37.176/37.612/38.427 ms
```
3) 
```shell
djnew@HOME_PC:~$ docker ps -a
CONTAINER ID   IMAGE                       COMMAND                  CREATED          STATUS                     PORTS                                                                                                                                NAMES
0477f59098e9   busybox                     "ping -w 7 netology.…"   11 seconds ago   Exited (0) 2 seconds ago                                                                                                                                        pinger
c2dd8954f98f   nlkoz-nginx:latest          "/docker-entrypoint.…"   10 hours ago     Up 10 hours                80/tcp, 0.0.0.0:443->443/tcp, :::443->443/tcp                                                                                        app_nginx_lkoz
ee7a0a4605ba   nlkoz-dev80-dev:latest      ".docker/php/dev/doc…"   10 hours ago     Up 5 hours                 9000/tcp                                                                                                                             app_dev80_lkoz
0cd955eb3051   postgres:alpine             "docker-entrypoint.s…"   10 hours ago     Up 10 hours                0.0.0.0:5432->5432/tcp, :::5432->5432/tcp                                                                                            pgdb_lkoz
bebb8dd42b66   redis                       "docker-entrypoint.s…"   10 hours ago     Up 10 hours                0.0.0.0:6379->6379/tcp, :::6379->6379/tcp                                                                                            redis_lkoz
d3f4a23b8126   rabbitmq:3.6.6-management   "docker-entrypoint.s…"   10 hours ago     Up 10 hours                4369/tcp, 5671/tcp, 0.0.0.0:5672->5672/tcp, :::5672->5672/tcp, 15671/tcp, 25672/tcp, 0.0.0.0:15672->15672/tcp, :::15672->15672/tcp   rabbit_lkoz
b0d2d479e6eb   saas_app                    "docker-php-entrypoi…"   4 days ago       Exited (0) 4 days ago                                                                                                                                           bd-app
4cdbf3225fc0   postgres:9.6                "docker-entrypoint.s…"   4 days ago       Exited (0) 4 days ago
```
4) 
```shell
djnew@HOME_PC:~$ docker logs -f -t pinger
2021-09-27T15:34:41.715622836Z PING netology.ru (104.22.49.171): 56 data bytes
2021-09-27T15:34:41.753193370Z 64 bytes from 104.22.49.171: seq=0 ttl=37 time=37.471 ms
2021-09-27T15:34:42.753698191Z 64 bytes from 104.22.49.171: seq=1 ttl=37 time=37.899 ms
2021-09-27T15:34:43.753244808Z 64 bytes from 104.22.49.171: seq=2 ttl=37 time=37.295 ms
2021-09-27T15:34:44.753629977Z 64 bytes from 104.22.49.171: seq=3 ttl=37 time=37.570 ms
2021-09-27T15:34:45.753310754Z 64 bytes from 104.22.49.171: seq=4 ttl=37 time=37.145 ms
2021-09-27T15:34:46.753648252Z 64 bytes from 104.22.49.171: seq=5 ttl=37 time=37.368 ms
2021-09-27T15:34:47.753586513Z 64 bytes from 104.22.49.171: seq=6 ttl=37 time=37.210 ms
2021-09-27T15:34:48.716433406Z
2021-09-27T15:34:48.716465596Z --- netology.ru ping statistics ---
2021-09-27T15:34:48.716467810Z 7 packets transmitted, 7 packets received, 0% packet loss
2021-09-27T15:34:48.716469523Z round-trip min/avg/max = 37.145/37.422/37.899 ms
```
5) 
```shell
djnew@HOME_PC:~$ docker start pinger
pinger
```
6)
```shell
djnew@HOME_PC:~$ docker ps -a
CONTAINER ID   IMAGE                       COMMAND                  CREATED         STATUS                          PORTS                                                                                                                                NAMES
0477f59098e9   busybox                     "ping -w 7 netology.…"   4 minutes ago   Exited (0) About a minute ago                                                                                                                                        pinger
c2dd8954f98f   nlkoz-nginx:latest          "/docker-entrypoint.…"   10 hours ago    Up 10 hours                     80/tcp, 0.0.0.0:443->443/tcp, :::443->443/tcp                                                                                        app_nginx_lkoz
ee7a0a4605ba   nlkoz-dev80-dev:latest      ".docker/php/dev/doc…"   10 hours ago    Up 5 hours                      9000/tcp                                                                                                                             app_dev80_lkoz
0cd955eb3051   postgres:alpine             "docker-entrypoint.s…"   10 hours ago    Up 10 hours                     0.0.0.0:5432->5432/tcp, :::5432->5432/tcp                                                                                            pgdb_lkoz
bebb8dd42b66   redis                       "docker-entrypoint.s…"   10 hours ago    Up 10 hours                     0.0.0.0:6379->6379/tcp, :::6379->6379/tcp                                                                                            redis_lkoz
d3f4a23b8126   rabbitmq:3.6.6-management   "docker-entrypoint.s…"   10 hours ago    Up 10 hours                     4369/tcp, 5671/tcp, 0.0.0.0:5672->5672/tcp, :::5672->5672/tcp, 15671/tcp, 25672/tcp, 0.0.0.0:15672->15672/tcp, :::15672->15672/tcp   rabbit_lkoz
b0d2d479e6eb   saas_app                    "docker-php-entrypoi…"   4 days ago      Exited (0) 4 days ago                                                                                                                                                bd-app
4cdbf3225fc0   postgres:9.6                "docker-entrypoint.s…"   4 days ago      Exited (0) 4 days a
```
7)
```shell
djnew@HOME_PC:~$ docker logs -f -t pinger
2021-09-27T15:34:41.715622836Z PING netology.ru (104.22.49.171): 56 data bytes
2021-09-27T15:34:41.753193370Z 64 bytes from 104.22.49.171: seq=0 ttl=37 time=37.471 ms
2021-09-27T15:34:42.753698191Z 64 bytes from 104.22.49.171: seq=1 ttl=37 time=37.899 ms
2021-09-27T15:34:43.753244808Z 64 bytes from 104.22.49.171: seq=2 ttl=37 time=37.295 ms
2021-09-27T15:34:44.753629977Z 64 bytes from 104.22.49.171: seq=3 ttl=37 time=37.570 ms
2021-09-27T15:34:45.753310754Z 64 bytes from 104.22.49.171: seq=4 ttl=37 time=37.145 ms
2021-09-27T15:34:46.753648252Z 64 bytes from 104.22.49.171: seq=5 ttl=37 time=37.368 ms
2021-09-27T15:34:47.753586513Z 64 bytes from 104.22.49.171: seq=6 ttl=37 time=37.210 ms
2021-09-27T15:34:48.716433406Z
2021-09-27T15:34:48.716465596Z --- netology.ru ping statistics ---
2021-09-27T15:34:48.716467810Z 7 packets transmitted, 7 packets received, 0% packet loss
2021-09-27T15:34:48.716469523Z round-trip min/avg/max = 37.145/37.422/37.899 ms
2021-09-27T15:38:22.905841155Z PING netology.ru (104.22.49.171): 56 data bytes
2021-09-27T15:38:22.943337081Z 64 bytes from 104.22.49.171: seq=0 ttl=37 time=37.435 ms
2021-09-27T15:38:23.943795796Z 64 bytes from 104.22.49.171: seq=1 ttl=37 time=37.661 ms
2021-09-27T15:38:24.943677051Z 64 bytes from 104.22.49.171: seq=2 ttl=37 time=37.455 ms
2021-09-27T15:38:25.943986055Z 64 bytes from 104.22.49.171: seq=3 ttl=37 time=37.552 ms
2021-09-27T15:38:26.944494342Z 64 bytes from 104.22.49.171: seq=4 ttl=37 time=37.957 ms
2021-09-27T15:38:27.943958537Z 64 bytes from 104.22.49.171: seq=5 ttl=37 time=37.236 ms
2021-09-27T15:38:28.944361255Z 64 bytes from 104.22.49.171: seq=6 ttl=37 time=37.529 ms
2021-09-27T15:38:29.906908457Z
2021-09-27T15:38:29.906957840Z --- netology.ru ping statistics ---
2021-09-27T15:38:29.906961767Z 7 packets transmitted, 7 packets received, 0% packet loss
2021-09-27T15:38:29.906964252Z round-trip min/avg/max = 37.236/37.546/37.957 ms
```
8) 2 запуска, 12 запросов
9) 
```shell
djnew@HOME_PC:~$ docker container rm pinger
pinger
```
9)
```shell
djnew@HOME_PC:~$ docker rmi busybox
Untagged: busybox:latest
```
