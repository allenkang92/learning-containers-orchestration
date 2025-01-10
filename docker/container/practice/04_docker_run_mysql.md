# 4. MySQL 컨테이너 실행

이번에는 도커를 이용하여 MySQL 데이터베이스 컨테이너를 실행하는 방법에 대해 알아보겠습니다. MySQL 컨테이너를 실행할 때는 데이터베이스의 루트 비밀번호와 같은 중요한 설정들을 환경 변수를 통해 지정할 수 있습니다.

## 4.1 기본 실행

### 4.1.1 컨테이너 생성
다음 명령어를 사용하여 `mysql_db`라는 이름의 MySQL 컨테이너를 생성하고 실행합니다.

```bash
docker run -d \
  --name mysql_db \
  -e MYSQL_ROOT_PASSWORD=secret \
  -p 3306:3306 \
  mysql:latest
```

옵션 설명:

- `-d`: 컨테이너를 백그라운드에서 실행합니다.
- `--name mysql_db`: 생성될 컨테이너의 이름을 `mysql_db`로 지정합니다.
- `-e MYSQL_ROOT_PASSWORD=secret`: 환경 변수를 설정하는 옵션입니다. 여기서는 `MYSQL_ROOT_PASSWORD`라는 환경 변수에 `secret`라는 값을 할당합니다. 이는 MySQL 컨테이너의 루트 사용자 비밀번호를 설정하는 데 사용됩니다.
- `-p 3306:3306`: 호스트의 3306번 포트와 컨테이너의 3306번 포트를 연결합니다.
- `mysql:latest`: 사용할 이미지의 이름입니다. 별도의 태그(버전)를 지정하지 않았으므로 도커는 자동으로 최신 버전(latest)의 MySQL 이미지를 다운로드하여 사용합니다.

### 4.1.2 상태 확인
`docker ps` 명령어를 사용하여 `mysql_db` 컨테이너가 정상적으로 실행 중인지 확인할 수 있습니다.

```bash
docker ps | grep mysql_db
```

실행 결과에서 `mysql_db`라는 이름의 컨테이너가 목록에 나타나고, STATUS 항목의 값이 Up으로 표시되면 컨테이너가 성공적으로 실행 중인 것입니다.

## 4.2 데이터베이스 관리

### 4.2.1 MySQL 접속
다음 명령어를 사용하여 `mysql_db` 컨테이너에 접속할 수 있습니다.

```bash
docker exec -it mysql_db mysql -uroot -p
```

### 4.2.2 데이터베이스 생성
다음 SQL 명령어를 사용하여 데이터베이스를 생성할 수 있습니다.

```sql
CREATE DATABASE myapp;
USE myapp;
```

## 4.3 데이터 지속성

### 4.3.1 볼륨 생성
다음 명령어를 사용하여 볼륨을 생성할 수 있습니다.

```bash
docker volume create mysql_data
```

### 4.3.2 볼륨 마운트
다음 명령어를 사용하여 볼륨을 마운트할 수 있습니다.

```bash
docker run -d \
  --name mysql_persistent \
  -e MYSQL_ROOT_PASSWORD=secret \
  -v mysql_data:/var/lib/mysql \
  -p 3307:3306 \
  mysql:latest
```

## 4.4 환경 설정

### 4.4.1 설정 파일 마운트
다음 명령어를 사용하여 설정 파일을 마운트할 수 있습니다.

```bash
docker run -d \
  --name mysql_custom \
  -e MYSQL_ROOT_PASSWORD=secret \
  -v /host/my.cnf:/etc/mysql/my.cnf:ro \
  -p 3308:3306 \
  mysql:latest
```

### 4.4.2 환경 변수 설정
다음 명령어를 사용하여 환경 변수를 설정할 수 있습니다.

```bash
docker run -d \
  --name mysql_env \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=myapp \
  -e MYSQL_USER=myuser \
  -e MYSQL_PASSWORD=mypass \
  -p 3309:3306 \
  mysql:latest
```

## 4.5 백업과 복구

### 4.5.1 데이터베이스 백업
다음 명령어를 사용하여 데이터베이스를 백업할 수 있습니다.

```bash
docker exec mysql_db \
  mysqldump -uroot -p myapp > backup.sql
```

### 4.5.2 데이터베이스 복구
다음 명령어를 사용하여 데이터베이스를 복구할 수 있습니다.

```bash
docker exec -i mysql_db \
  mysql -uroot -p myapp < backup.sql