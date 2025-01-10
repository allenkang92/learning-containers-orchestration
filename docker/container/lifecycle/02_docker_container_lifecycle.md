# 2. 도커 컨테이너 생명주기

## 2.1 컨테이너 상태

### 2.1.1 기본 상태
- Created: 생성됨
- Running: 실행 중
- Paused: 일시 중지됨
- Stopped: 정지됨
- Deleted: 삭제됨

### 2.1.2 상태 전이
- Created → Running: start
- Running → Paused: pause
- Paused → Running: unpause
- Running → Stopped: stop
- Stopped → Running: restart

## 2.2 컨테이너 생성과 시작

### 2.2.1 컨테이너 생성
```bash
docker create [옵션] 이미지[:태그]
```

### 2.2.2 컨테이너 시작
```bash
docker start 컨테이너_이름
```

### 2.2.3 생성과 시작 동시 실행
```bash
docker run [옵션] 이미지[:태그]
```

## 2.3 컨테이너 중지와 삭제

### 2.3.1 컨테이너 중지
```bash
docker stop [옵션] 컨테이너_이름
```

### 2.3.2 컨테이너 강제 중지
```bash
docker kill 컨테이너_이름
```

### 2.3.3 컨테이너 삭제
```bash
docker rm [옵션] 컨테이너_이름
```

## 2.4 컨테이너 자동 재시작

### 2.4.1 재시작 정책
- no: 자동 재시작 안 함
- on-failure: 오류 시에만 재시작
- always: 항상 재시작
- unless-stopped: 수동 중지 전까지 재시작

### 2.4.2 재시작 설정
```bash
docker run --restart=always 이미지
```

## 2.5 컨테이너 업데이트 전략

### 2.5.1 롤링 업데이트
- 순차적 업데이트
- 무중단 서비스 유지
- 리소스 효율적 사용

### 2.5.2 블루-그린 배포
- 두 버전 동시 운영
- 즉시 롤백 가능
- 리소스 사용량 증가