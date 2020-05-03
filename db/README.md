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

## docker-compose 실행
```sh
$ docker-compose up -d
```

<hr>
<br>

## User 생성
```sh
$ docker exec -it oracle11g sqlplus
Enter user-name: system
Enter password: system
SQL> CREATE TABLESPACE DEV_SPACE DATAFILE 'sis.dat' SIZE 500M AUTOEXTEND ON NEXT 10M;
SQL> DEFINE NEW_USER = 'sis_user01';
SQL> CREATE USER &NEW_USER. IDENTIFIED BY "1234";
SQL> GRANT CONNECT, RESOURCE, CREATE JOB, CREATE VIEW, CREATE ANY CONTEXT TO &NEW_USER;
SQL> ALTER USER &NEW_USER QUOTA UNLIMITED ON USERS;
SQL> ALTER USER &NEW_USER DEFAULT TABLESPACE DEV_SPACE;
```

<hr>
<br>

## docker-compose 중지
```sh
$ docker-compose stop
```

<hr>
<br>

## docker-compose 프로세스 확인
```sh
$ docker-compose ps

          Name                 Command        State     Ports
-------------------------------------------------------------
firstproject_oracle11g_1   /entrypoint.sh    Exit 137
```

<hr>
<br>

## docker-compose 삭제
```sh
$ docker-compose rm
```

<hr>
<br>

## docker-compose 재시작
```sh
$ docker-compose up -d
```