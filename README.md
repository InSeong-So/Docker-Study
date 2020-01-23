# Docker
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
