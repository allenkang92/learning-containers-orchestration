# 1. 도커 컨테이너 파일 작업

## 1.1 파일 복사

### 1.1.1 호스트에서 컨테이너로 복사
```bash
docker cp /host/path container_name:/container/path
```

### 1.1.2 컨테이너에서 호스트로 복사
```bash
docker cp container_name:/container/path /host/path
```

## 1.2 볼륨 마운트

### 1.2.1 바인드 마운트
```bash
docker run -v /host/path:/container/path image_name
```

### 1.2.2 볼륨 생성 및 사용
```bash
docker volume create volume_name
docker run -v volume_name:/container/path image_name
```

## 1.3 파일 권한

### 1.3.1 읽기 전용 마운트
```bash
docker run -v /host/path:/container/path:ro image_name
```

### 1.3.2 권한 변경
```bash
docker exec container_name chmod 644 /path/to/file
```

## 1.4 파일 시스템 검사

### 1.4.1 컨테이너 내부 파일 목록
```bash
docker exec container_name ls -la /path
```

### 1.4.2 볼륨 정보 확인
```bash
docker volume inspect volume_name