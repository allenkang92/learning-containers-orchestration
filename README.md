
# learning-containers-orchestration 
## 컨테이너와 오케스트레이션 학습 가이드

컨테이너 기술의 기초부터 오케스트레이션까지 단계별로 학습할 수 있도록 구성된 문서들이긴 합니다...

## 학습 로드맵

1. **Docker 기초** (`/docker`)
   - 컨테이너의 기본 개념
   - 이미지와 컨테이너 다루기
   - 네트워크와 볼륨 관리
   - 실전 활용 예제

2. **Docker Compose** (`/docker-compose`)
   - 다중 컨테이너 애플리케이션 관리
   - docker-compose.yml 작성법
   - 기본 명령어와 활용

3. **Kubernetes** (`/kubernetes`)
   - 쿠버네티스 기본 개념
   - 클러스터 아키텍처
   - 핵심 컴포넌트 이해
   - 실습 예제

## 디렉토리 구조
```
.
├── docker/                 # Docker 학습 자료
│   ├── basics/            # 기본 개념
│   ├── container/         # 컨테이너 관리
│   ├── image/            # 이미지 관리
│   ├── network/          # 네트워크 설정
│   └── volume/           # 볼륨 관리
│
├── docker-compose/        # Docker Compose 학습 자료
│   ├── 01_introduction.md
│   ├── 02_file_structure.md
│   └── 03_commands.md
│
├── kubernetes/           # Kubernetes 학습 자료
│   ├── basics/          # 기본 개념
│   ├── architecture/    # 시스템 구조
│   ├── components/      # 핵심 컴포넌트
│   └── practice/        # 실습 예제
│
└── requirements.txt     # 필요한 패키지 목록
```

## 시작하기

1. 필요한 도구 설치:
   ```bash
   pip install -r requirements.txt
   ```

2. Docker 설치:
   - [Docker Desktop](https://www.docker.com/products/docker-desktop) 설치
   - Docker Engine 실행 확인
   
## 필요 사항

- Python 3.6 이상
- Docker Engine
- Kubernetes (Docker Desktop의 Kubernetes 또는 minikube)

## 문서 구성

각 섹션은 다음과 같이 구성되어 있습니다:
- 개념 설명
- 실습 예제
- 명령어 가이드
- 문제 해결 팁
