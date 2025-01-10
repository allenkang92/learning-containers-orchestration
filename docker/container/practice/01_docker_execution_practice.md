# 1. 도커 실행 연습

## 1.1 기본 실행

### 1.1.1 Ubuntu 컨테이너
```bash
docker run ubuntu:latest echo "Hello, Docker!"
```

### 1.1.2 Nginx 웹 서버
```bash
docker run -d -p 80:80 nginx:latest
```

## 1.2 대화형 실행

### 1.2.1 Ubuntu 셸 접속
```bash
docker run -it ubuntu:latest /bin/bash
```

### 1.2.2 CentOS 셸 접속
```bash
docker run -it centos:latest /bin/bash
```

## 1.3 백그라운드 실행

### 1.3.1 데이터베이스 서버
```bash
docker run -d --name mysql-server \
  -e MYSQL_ROOT_PASSWORD=secret \
  mysql:latest
```

### 1.3.2 웹 애플리케이션
```bash
docker run -d --name webapp \
  -p 8080:80 \
  nginx:latest
```

## 1.4 볼륨 마운트

### 1.4.1 호스트 디렉토리 마운트
```bash
docker run -v /host/path:/container/path \
  ubuntu:latest
```

### 1.4.2 데이터 볼륨 사용
```bash
docker volume create mydata
docker run -v mydata:/data ubuntu:latest
```

## 1.5 네트워크 설정

### 1.5.1 포트 포워딩
```bash
docker run -p 8080:80 -p 443:443 nginx:latest
```

### 1.5.2 네트워크 연결
```bash
docker network create mynet
docker run --network mynet nginx:latest
```

## 1.6 명명된 Nginx 컨테이너 실행 및 관리
컨테이너에 이름을 지정하고 백그라운드에서 실행하며, 포트 매핑을 설정하는 방법
docker run --name my_nginx -d -p 8080:80 nginx

옵션 설명:

--name my_nginx: 컨테이너의 이름을 my_nginx로 지정합니다.

-d: 컨테이너를 백그라운드에서 실행합니다.

-p 8080:80: 호스트의 8080 포트를 컨테이너의 80 포트에 매핑합니다. 이를 통해 호스트의 8080 포트로 접속하면 컨테이너 내부의 Nginx 서버에 접근할 수 있습니다.

nginx: 사용할 이미지의 이름입니다. 버전을 명시하지 않으면 최신 버전(latest)이 사용됩니다.

## 1.7 컨테이너 정지
실행 중인 my_nginx 컨테이너를 정지
docker stop my_nginx

docker stop 명령어는 지정된 컨테이너에 SIGTERM 신호를 보내 정상적으로 종료하도록 요청합니다.

컨테이너가 정지되었는지 확인하려면 docker ps 명령어를 실행합니다. 정지된 컨테이너는 목록에 나타나지 않습니다.
docker ps

## 1.8 정지된 컨테이너 확인
모든 컨테이너 목록을 확인하여 my_nginx 컨테이너가 정지 상태로 존재하는지 확인합니다.

docker ps -a

-a 옵션은 실행 중인 컨테이너뿐만 아니라 모든 컨테이너(정지된 컨테이너 포함)를 표시합니다. STATUS 항목이 Exited로 표시되면 컨테이너가 종료된 상태임을 의미합니다.

## 1.9 컨테이너 삭제
정지된 my_nginx 컨테이너를 삭제합니다.

docker rm my_nginx

docker rm 명령어는 지정된 컨테이너를 완전히 삭제합니다.

컨테이너가 삭제되었는지 확인하려면 docker ps -a 명령어를 다시 실행합니다. 삭제된 컨테이너는 목록에 나타나지 않습니다.

docker ps -a

도커 명령어 실행 중 문제가 발생하면 다음 사항들을 확인해 보세요.

오타 확인: 명령어 철자에 오타가 있는지 확인합니다.

공백 및 개행: 불필요한 공백이나 개행이 포함되었는지 확인합니다.

옵션 및 공백: - 기호나 옵션 간의 공백이 빠지지 않았는지 확인합니다.

대소문자: 명령어와 옵션의 대소문자가 올바른지 확인합니다.

하이픈과 언더바: 하이픈(-)과 언더바(_)가 혼동되어 사용되지는 않았는지 확인합니다.

도커 명령어는 오타에 민감하므로 주의 깊게 입력하는 것이 중요합니다. 실수를 줄이기 위해 입력 후 다시 한번 확인하는 습관을 들이는 것이 좋습니다.

## 1.10 컨테이너 ID를 이용한 작업
docker stop 또는 docker rm과 같이 컨테이너 이름을 지정해야 하는 명령어는 컨테이너 ID 또는 ID의 앞 몇 글자를 사용하여 실행할 수도 있습니다.

docker stop <컨테이너 ID>
docker rm <컨테이너 ID>

컨테이너 ID는 docker ps -a 명령어를 통해 확인할 수 있으며, ID의 앞 몇 글자만으로도 컨테이너를 식별할 수 있습니다 (ID가 고유하다면).