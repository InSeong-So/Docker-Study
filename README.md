# Docker
## 보유중인 docker images
|REPOSITORY                    |   TAG             |    IMAGE ID         |   CREATED           |  SIZE|
|-|-|-|-|-|
|garethflowers/svn-server        | latest            |  db3e45868785       | 3 weeks ago         |14.2MB|
|mcr.microsoft.com/mssql/server  | 2017-latest       |  cfe5615bf6a8       | 4 months ago        |1.38GB|
|mariadb                        |  10.3             |   b468922dbbd7      |  14 months ago      | 366MB|
|postgres                       |  11.1             |   8d84c7940aa6      |  14 months ago      | 311MB|
|jaspeen/oracle-xe-11g          |  latest           |   52fbd1fe2d7a      |  4 years ago        | 792MB|
|jaspeen/oracle-11g             |  latest           |   0c8711fe4f0f      |  4 years ago        | 281MB|
|deepdiver/docker-oracle-xe-11g |  latest           |   396b3e06a5dc      |  4 years ago        | 2.7GB|

## Docker 설치
```sh
#설치 :
yum install -y docker

#또는
curl -fsSL https://get.docker.com/

#실행 :
systemctl start docker
systemctl enable docker
```

<hr>
<br>

## Docker-Compose 설치
```sh
#설치 :
curl -L https://github.com/docker/compose/releases/download/1.23.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

#권한 부여 :
chmod +x /usr/local/bin/docker-compose

#버전 확인 :
docker-compose --version

#실행 :
docker-compose up -d
```

<hr>
<br>

## Docker SVN 설치 및 설정
```sh
# 도커 이미지 pull 및 컨테이너 설치
docker run --name svn-server --detach --volume Documents/workspace/SVN --publish 3690:3690 garethflowers/svn-server

# 구동 확인
docker ps -a

# 생성된 컨테이너 내부에 svn 저장소 추가 ( vue-repo 라는 이름의 저장소 )
docker exec -it svn-server svnadmin create vue-repo

# 추가한 svn 저장소의 정보 확인
docker exec -it svn-server svnadmin info vue-repo

# 생성된 svn 컨테이너로 이동
docker exec -it svn-server sh

# svn 계정 추가
vi /var/opt/svn/vue-repo/conf/passwd

# svn 권한 설정
vi /var/opt/svn/vue-repo/conf/authz

# svn 서버의 전반적인 설정
vi /var/opt/svn/vue-repo/conf/svnserve.conf 
```

<hr>
<br>

## DB 컨테이너 설치
### oracle
```sh
# 도커 이미지 pull 및 컨테이너 설치
docker run --name oracle -d -p 1521:1521 jaspeen/oracle-xe-11g

# 설치한 컨테이너 실행 및 sqlplus 실행
docker exec -it oracle sqlplus

# user-name 입력
user-name: system

# password 입력
password: oracle

# 프로그레스가 실행되지 않은 상태라 뜨는 에러이므로 조금 대기하면 정상 동작
ORA-01089: immediate shutdown in progress 
```

<hr>
<br>
