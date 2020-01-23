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