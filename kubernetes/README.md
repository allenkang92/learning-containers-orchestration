# Kubernetes 학습 가이드

Kubernetes(쿠버네티스)의 기본 개념들과 진자 간단한 실습까지 할 수 있도록 문서들을 작성해뒀습니다.

## 디렉토리 구조

```
kubernetes/
├── basics/              # 기본 개념
│   ├── 01_kubernetes_introduction.md    # 쿠버네티스 소개
│   └── 02_container_orchestration.md    # 컨테이너 오케스트레이션 개념
│
├── architecture/        # 아키텍처
│   └── 01_master_worker_nodes.md        # 마스터/워커 노드 구조
│
├── components/         # 핵심 컴포넌트
│   ├── 01_pods.md                       # 파드
│   ├── 02_services.md                   # 서비스
│   ├── 03_deployments.md                # 디플로이먼트
│   └── 04_replicasets.md                # 레플리카셋
│
└── practice/          # 실습
    ├── 01_basic_commands.md             # 기본 명령어
    ├── 02_deployment_practice.md        # 디플로이먼트 실습
    ├── 03_service_networking.md         # 서비스/네트워킹 실습
    └── examples/                        # 예제 YAML 파일
```

## 학습 순서

1. **기초 개념 학습** (`basics/`)
   - 쿠버네티스가 무엇인지 이해
   - 컨테이너 오케스트레이션의 필요성과 개념 학습

2. **아키텍처 이해** (`architecture/`)
   - 쿠버네티스 클러스터 구조 파악
   - 마스터 노드와 워커 노드의 역할 이해

3. **핵심 컴포넌트 학습** (`components/`)
   - 파드, 서비스, 디플로이먼트, 레플리카셋 등 주요 개념 학습
   - 각 컴포넌트의 역할과 관계 이해

4. **실습** (`practice/`)
   - 기본 kubectl 명령어 익히기
   - 실제 애플리케이션 배포 실습
   - 서비스 생성 및 네트워킹 구성 실습

## 시작하기

1. 필요한 도구 설치:
   ```bash
   pip install -r requirements.txt
   ```

2. 쿠버네티스 환경 준비:
   - Docker Desktop의 Kubernetes 활성화 또는
   - minikube 설치

3. 기본 개념부터 순차적으로 학습 진행

## 실습 환경

- Kubernetes 클라이언트 버전: v1.18.0 이상
- Python 3.6 이상
- 필요한 Python 패키지는 requirements.txt 참조

## 참고 사항

- 각 문서는 실습 예제를 포함하고 있습니다.
- `examples/` 디렉토리의 YAML 파일들은 실습에서 사용됩니다.
- 문제 해결과 디버깅 가이드도 포함되어 있습니다.

## 기여하기

- 오타 수정이나 내용 개선은 Pull Request 환영
- 새로운 예제나 실습 시나리오 제안도 가능
