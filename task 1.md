1. Загрузите образ busybox последней версии;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker -v
Docker version 27.3.1, build ce12230
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker pull busybox
Using default tag: latest
latest: Pulling from library/busybox
430378704d12: Pull complete
Digest: sha256:db142d433cdde11f10ae479dbf92f3b13d693fd1c91053da9979728cceb1dc68
Status: Downloaded newer image for busybox:latest
docker.io/library/busybox:latest

2. Запустите новый контейнер busybox с командой ping сайта netology.ru, и количеством пингов 7, поименуйте контейнер pinger;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker run --name pinger busybox ping -c 7 netology.ru
PING netology.ru (104.22.41.171): 56 data bytes
64 bytes from 104.22.41.171: seq=0 ttl=63 time=161.891 ms
64 bytes from 104.22.41.171: seq=2 ttl=63 time=50.782 ms
64 bytes from 104.22.41.171: seq=3 ttl=63 time=50.403 ms
64 bytes from 104.22.41.171: seq=4 ttl=63 time=54.050 ms
64 bytes from 104.22.41.171: seq=5 ttl=63 time=51.578 ms

--- netology.ru ping statistics ---
7 packets transmitted, 7 packets received, 0% packet loss
round-trip min/avg/max = 50.403/71.549/161.891 ms

3. Выведите на список всех контейнеров - запущенных и остановленных;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                      PORTS     
NAMES
1d41d519fcc5   busybox   "ping -c 7 netology.…"   40 seconds ago   Exited (0) 31 seconds ago
pinger

4. Выведите на экран логи контейнера с именем pinger;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker logs -f -t pinger
2024-12-06T18:50:57.502450922Z PING netology.ru (104.22.41.171): 56 data bytes
2024-12-06T18:50:57.502526815Z 64 bytes from 104.22.41.171: seq=0 ttl=63 time=161.891 ms
2024-12-06T18:50:59.391979135Z 64 bytes from 104.22.41.171: seq=2 ttl=63 time=50.782 ms
2024-12-06T18:51:01.395719682Z 64 bytes from 104.22.41.171: seq=4 ttl=63 time=54.050 ms
2024-12-06T18:51:02.393521091Z 64 bytes from 104.22.41.171: seq=5 ttl=63 time=51.578 ms
2024-12-06T18:51:03.401225551Z 64 bytes from 104.22.41.171: seq=6 ttl=63 time=59.071 ms
2024-12-06T18:51:03.407385160Z
2024-12-06T18:51:03.407428587Z 7 packets transmitted, 7 packets received, 0% packet loss
2024-12-06T18:51:03.407434790Z round-trip min/avg/max = 50.403/71.549/161.891 ms

5. Запустите второй раз контейнера с именем pinger;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker start pinger
pinger
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS                      PORTS     N
AMES
1d41d519fcc5   busybox   "ping -c 7 netology.…"   2 minutes ago   Exited (0) 30 seconds ago             p
inger

6. Выведите на список всех контейнеров - запущенных и остановленных;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS                      PORTS     N
AMES
1d41d519fcc5   busybox   "ping -c 7 netology.…"   2 minutes ago   Exited (0) 42 seconds ago             p
inger

7. Выведите на экран логи контейнера с именем pinger;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker logs -f -t pinger
2024-12-06T18:50:57.502450922Z PING netology.ru (104.22.41.171): 56 data bytes
2024-12-06T18:50:57.502526815Z 64 bytes from 104.22.41.171: seq=0 ttl=63 time=161.891 ms
2024-12-06T18:50:58.414019672Z 64 bytes from 104.22.41.171: seq=1 ttl=63 time=73.072 ms
2024-12-06T18:50:59.391979135Z 64 bytes from 104.22.41.171: seq=2 ttl=63 time=50.782 ms
2024-12-06T18:51:00.391821829Z 64 bytes from 104.22.41.171: seq=3 ttl=63 time=50.403 ms
2024-12-06T18:51:01.395719682Z 64 bytes from 104.22.41.171: seq=4 ttl=63 time=54.050 ms
2024-12-06T18:51:02.393521091Z 64 bytes from 104.22.41.171: seq=5 ttl=63 time=51.578 ms
2024-12-06T18:51:03.401225551Z 64 bytes from 104.22.41.171: seq=6 ttl=63 time=59.071 ms
2024-12-06T18:51:03.407385160Z
2024-12-06T18:51:03.407421834Z --- netology.ru ping statistics ---
2024-12-06T18:51:03.407428587Z 7 packets transmitted, 7 packets received, 0% packet loss
2024-12-06T18:51:03.407434790Z round-trip min/avg/max = 50.403/71.549/161.891 ms
2024-12-06T18:52:35.670197508Z PING netology.ru (104.22.41.171): 56 data bytes
2024-12-06T18:52:35.670259852Z 64 bytes from 104.22.41.171: seq=0 ttl=63 time=51.751 ms
2024-12-06T18:52:37.669498320Z 64 bytes from 104.22.41.171: seq=2 ttl=63 time=50.687 ms
2024-12-06T18:52:39.683431823Z 64 bytes from 104.22.41.171: seq=4 ttl=63 time=63.996 ms
2024-12-06T18:52:40.689723928Z 64 bytes from 104.22.41.171: seq=5 ttl=63 time=69.864 ms
2024-12-06T18:52:41.687159863Z 64 bytes from 104.22.41.171: seq=6 ttl=63 time=66.664 ms
2024-12-06T18:52:41.687220003Z
2024-12-06T18:52:41.687233270Z --- netology.ru ping statistics ---
2024-12-06T18:52:41.687248701Z 7 packets transmitted, 7 packets received, 0% packet loss
2024-12-06T18:52:41.687261617Z round-trip min/avg/max = 50.068/57.615/69.864 ms

8. Удалите контейнер с именем pinger;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker rm pinger
pinger

9. Определите по логам общее количество запусков команды ping и какое общее количество отправленых запросов;
2024-12-06T18:51:03.407421834Z --- netology.ru ping statistics ---
2024-12-06T18:51:03.407428587Z 7 packets transmitted, 7 packets received, 0% packet loss
2024-12-06T18:52:41.687233270Z --- netology.ru ping statistics ---
2024-12-06T18:52:41.687248701Z 7 packets transmitted, 7 packets received, 0% packet loss
Ответ: 2 запуска, 14 запросов суммарно

10. Удалите образ busybox;
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> docker rmi busybox
Untagged: busybox:latest
Untagged: busybox@sha256:db142d433cdde11f10ae479dbf92f3b13d693fd1c91053da9979728cceb1dc68
Deleted: sha256:517b897a6a8312ce202a85c8a517d820b0fc5b6f5d14ec2a3267906f75680403
Deleted: sha256:dab88e68d7096681d624de8bd542df9d91bae06c739a73483b6fb0e6869421ea
PS C:\Users\поль\RAB\NDSE\NDSE-docker09> ^C
PS C:\Users\поль\RAB\NDSE\NDSE-docker09>