1) 
```shell
djnew@HOME_PC:~$ docker pull node:15.14
15.14: Pulling from library/node
bfde2ec33fbc: Pull complete
787f5e2f1047: Pull complete
7b6173a10eb8: Pull complete
dc05be471d51: Pull complete
55fab5cadd3c: Pull complete
bd821d20ef8c: Pull complete
6041b69671c6: Pull complete
989c5d2d2313: Pull complete
4b57d41e8391: Pull complete
Digest: sha256:608bba799613b1ebf754034ae008849ba51e88b23271412427b76d60ae0d0627
Status: Downloaded newer image for node:15.14
docker.io/library/node:15.14
```
2) 
```shell
djnew@HOME_PC:~/netology$ docker run -i -d --name first_node -v ~/netology:/var/first/data node:15.14 node
4a056f384bbcf7856ffa9d2458459fe6b50e53889e66816326719683aa294947
```
3
```shell
djnew@HOME_PC:~/netology$ docker run -i -d --name second_node -v ~/netology:/var/second/data  node:15.14 node
bacd29afa893b5c8b0bb8ff30cc756196162985bf91b8766d46ae23f346521eb
```
4)
```shell
djnew@HOME_PC:~/netology$ docker exec -it first_node /bin/bash
root@4a056f384bbc:/# touch /var/first/data/test.txt
root@4a056f384bbc:/# exit
exit
```
5)
```shell
djnew@HOME_PC:~/netology$ ls -la > test1.txt
```
6)
```shell
djnew@HOME_PC:~/netology$ docker exec -it second_node /bin/bash
root@bacd29afa893:/# cd /var/second/data
root@bacd29afa893:/var/second/data# ls -la
total 12
drwxr-xr-x 2 node node 4096 Sep 27 17:37 .
drwxr-xr-x 3 root root 4096 Sep 27 17:33 ..
-rw-r--r-- 1 root root    0 Sep 27 17:36 test.txt
-rw-r--r-- 1 node node  208 Sep 27 17:38 test1.txt
root@bacd29afa893:/var/second/data# cat test
test.txt   test1.txt
root@bacd29afa893:/var/second/data# cat test.txt
root@bacd29afa893:/var/second/data# cat test1.txt
total 8
drwxr-xr-x  2 djnew djnew 4096 Sep 27 20:37 .
drwxr-xr-x 11 djnew djnew 4096 Sep 27 20:29 ..
-rw-r--r--  1 root  root     0 Sep 27 20:36 test.txt
-rw-r--r--  1 djnew djnew    0 Sep 27 20:38 test1.txt
```
7)
```shell
djnew@HOME_PC:~/netology$ docker stop first_node
first_node
djnew@HOME_PC:~/netology$ docker stop second_node
second_node
```
8)
```shell
djnew@HOME_PC:~/netology$ docker rm first_node
first_node
djnew@HOME_PC:~/netology$ docker rm second_node
second_node
```
9) 
```shell
djnew@HOME_PC:~/netology$ docker rmi node:15.14
Untagged: node:15.14
Untagged: node@sha256:608bba799613b1ebf754034ae008849ba51e88b23271412427b76d60ae0d0627
Deleted: sha256:3d3f41722daf1a77c34d6eade6676bbffa2d6a2a21095de2ab0c427a5c942fc9
Deleted: sha256:601382991a159cfc5013ad973158f30b7b7a913e8d7e547b3456deab3ad98022
Deleted: sha256:d5db49eecae8c02c9ea3a79f89c43ded9162bac118a0302a7b514d0df82aa112
Deleted: sha256:a2c1973858d0aad3de0927294602b17c8ef9050c30e0f461e0868997a08552a4
Deleted: sha256:a0153172017a08a521a8be971ca4dcb5fbc4b7227642c12bbb2da6265bd66b50
Deleted: sha256:f1123940e954d335d91b52a40fab4f8144f38ff113ade7d65663071d0f06da6f
Deleted: sha256:f1f4fbb0e7e6e0ce2d9eae1e577f9f6df0a719dd874bff00b2d08895c75c297d
Deleted: sha256:1eb455ab6d45fdbbd90fccff791ffa228080c052acf464f8da1b1d78650bd706
Deleted: sha256:1dbe832a694971a925d7d216f49b700c95f402bd72288f9d37eceb1d59dcf72d
Deleted: sha256:2f4ee6a2e1b5dfb9236cd262e788f9d39109242ca27a4aacb583c8af66ec3ff7
```
