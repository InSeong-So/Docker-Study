# Database : Oracle
## Docker-compose 설치
```sh
$ sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

<hr>
<br>

## 권한설정
```sh
$ sudo chmod +x /usr/local/bin/docker-compose
```

<hr>
<br>

## version 확인
```sh
$ docker-compose --version
```

<hr>
<br>

## docker-compose.yml 생성
```sh
$ touch docker-compose.yml

version: '2'
services:
  oracle11g:
    image: jaspeen/oracle-xe-11g
    container_name: oracle11g
    volumes:
      - ~/docker/data:/u01/app/oracle jaspeen/oracle-xe-11g
    ports:
      - 1521:1521
```