# 1. 도커 네트워크 명령어

## 1.1 네트워크 생성
```bash
docker network create [옵션] 네트워크_이름
```

### 1.1.1 주요 옵션
- `--driver`, `-d`: 네트워크 드라이버 지정 (기본값: bridge)
- `--subnet`: 서브넷 지정 (예: 172.18.0.0/16)
- `--gateway`: 게이트웨이 IP 지정
- `--ip-range`: IP 범위 지정
- `--attachable`: 외부 컨테이너가 연결할 수 있도록 설정

## 1.2 네트워크 목록 확인
```bash
docker network ls [옵션]
```

### 1.2.1 주요 옵션
- `--filter`, `-f`: 필터링 (예: driver=bridge)
- `--no-trunc`: 전체 ID 표시
- `--quiet`, `-q`: 네트워크 ID만 표시

## 1.3 네트워크 상세 정보
```bash
docker network inspect [옵션] 네트워크_이름
```

### 1.3.1 확인 가능한 정보
- 네트워크 ID
- 생성 일시
- 드라이버 종류
- 연결된 컨테이너 목록
- IPAM 구성
- 서브넷 정보

## 1.4 네트워크 삭제
```bash
docker network rm 네트워크_이름 [네트워크_이름...]
```

### 1.4.1 주의사항
- 사용 중인 네트워크는 삭제할 수 없음
- 여러 네트워크를 한 번에 삭제 가능

## 1.5 컨테이너 네트워크 연결/해제

### 1.5.1 네트워크 연결
```bash
docker network connect [옵션] 네트워크_이름 컨테이너_이름
```

#### 1.5.1.1 주요 옵션
- `--ip`: 특정 IP 주소 할당
- `--alias`: 네트워크 별칭 설정
- `--link`: 다른 컨테이너와 링크

### 1.5.2 네트워크 연결 해제
```bash
docker network disconnect [옵션] 네트워크_이름 컨테이너_이름
```

#### 1.5.2.1 주요 옵션
- `-f`, `--force`: 강제 연결 해제

## 1.6 네트워크 정리
```bash
docker network prune [옵션]
```

### 1.6.1 주요 옵션
- `--filter`: 필터링 조건 지정
- `-f`, `--force`: 확인 없이 강제 삭제