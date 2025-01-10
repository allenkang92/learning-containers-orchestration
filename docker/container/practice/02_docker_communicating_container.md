# 2. 도커 컨테이너 통신

## 2.1 네트워크 생성

### 2.1.1 사용자 정의 네트워크
```bash
docker network create mynetwork
```

### 2.1.2 네트워크 확인
```bash
docker network ls
```

## 2.2 컨테이너 생성 및 연결

### 2.2.1 첫 번째 컨테이너
```bash
docker run -d --name container1 \
  --network mynetwork \
  nginx:latest
```

### 2.2.2 두 번째 컨테이너
```bash
docker run -d --name container2 \
  --network mynetwork \
  nginx:latest
```

## 2.3 컨테이너 간 통신

### 2.3.1 DNS 조회
```bash
docker exec container1 ping container2
```

### 2.3.2 HTTP 통신
```bash
docker exec container1 curl http://container2
```

## 2.4 네트워크 관리

### 2.4.1 네트워크 연결
```bash
docker network connect mynetwork container3
```

### 2.4.2 네트워크 연결 해제
```bash
docker network disconnect mynetwork container3
```

## 2.5 네트워크 검사

### 2.5.1 네트워크 상세 정보
```bash
docker network inspect mynetwork
```

### 2.5.2 연결된 컨테이너 확인
```bash
docker network inspect mynetwork -f '{{range .Containers}}{{.Name}} {{end}}'