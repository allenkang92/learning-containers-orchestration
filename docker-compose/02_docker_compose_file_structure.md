# 2. 도커 컴포즈 파일 구조

## 2.1 기본 구조
```yaml
version: "3.8"
services:
  service1:
    # 서비스 설정
  service2:
    # 서비스 설정
networks:
  # 네트워크 설정
volumes:
  # 볼륨 설정
```

## 2.2 필수 요소

### 2.2.1 버전 정의
- `version`: 도커 컴포즈 파일 형식 버전
- 최신 버전 사용 권장 (현재 3.8)

### 2.2.2 서비스 정의
- `services`: 실행할 컨테이너들의 집합
- 각 서비스는 독립적인 컨테이너로 실행

## 2.3 서비스 설정

### 2.3.1 기본 설정
```yaml
services:
  webapp:
    image: nginx:latest
    container_name: my-webapp
    ports:
      - "80:80"
    environment:
      - NODE_ENV=production
```

### 2.3.2 빌드 설정
```yaml
services:
  webapp:
    build:
      context: ./dir
      dockerfile: Dockerfile.dev
      args:
        buildno: 1
```

### 2.3.3 네트워크 설정
```yaml
services:
  webapp:
    networks:
      - frontend
      - backend

networks:
  frontend:
    driver: bridge
  backend:
    driver: bridge
```

### 2.3.4 볼륨 설정
```yaml
services:
  db:
    volumes:
      - db-data:/var/lib/mysql
      - ./backup:/backup

volumes:
  db-data:
```

## 2.4 고급 설정

### 2.4.1 의존성 관리
```yaml
services:
  webapp:
    depends_on:
      - db
      - redis
```

### 2.4.2 배포 설정
```yaml
services:
  webapp:
    deploy:
      replicas: 3
      resources:
        limits:
          cpus: '0.50'
          memory: 50M
```

### 2.4.3 헬스체크
```yaml
services:
  webapp:
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost"]
      interval: 1m30s
      timeout: 10s
      retries: 3
```

## 2.5 작성 규칙

### 2.5.1 기본 규칙
- YAML 문법 준수
- 들여쓰기는 2칸 사용
- 서비스 이름은 영문 소문자와 하이픈 사용

### 2.5.2 환경 변수
- `.env` 파일 사용 권장
- 민감한 정보는 환경 변수로 관리

### 2.5.3 확장 필드
- `x-` 접두사로 시작하는 필드로 재사용 가능
- YAML 앵커와 별칭 활용