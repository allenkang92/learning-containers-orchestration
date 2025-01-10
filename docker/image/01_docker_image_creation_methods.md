# 컨테이너로 이미지 만들기

## 개요
컨테이너로 이미지를 만드는 방법은 두 가지가 있습니다:
1. 기존 컨테이너를 `commit` 명령어로 이미지로 변환하는 방법
2. Dockerfile 스크립트를 사용하여 새로운 이미지를 빌드하는 방법

## 컨테이너에서 이미지 만들기

### docker commit 사용
```bash
docker commit <컨테이너_이름> <새로운_이미지_이름>
```

#### 장점
- 기존 컨테이너를 사용하여 간단하게 이미지를 만들 수 있습니다.
- 컨테이너를 복제하거나 이동할 때 유용합니다.
- 단일 명령어만 필요합니다.

#### 한계
- 기존 컨테이너가 필요합니다.
- Dockerfile 방법보다 재현성이 떨어집니다.

## Dockerfile을 사용하여 이미지 만들기

### 기본 구조
- `FROM` 명령어로 베이스 이미지를 지정합니다.
- 컨테이너 구성에 대한 명령어를 추가합니다.
- `docker build` 명령어로 이미지를 빌드합니다.

### 빌드 명령어
```bash
docker build -t <이미지_이름> <빌드_컨텍스트_경로>
```

### 주요 Dockerfile 명령어

#### 베이스 이미지
- `FROM`: 베이스 이미지를 지정합니다.

#### 파일 연산
- `ADD`: 파일/폴더를 추가합니다.
- `COPY`: 파일/폴더를 이미지에 복사합니다.

#### 실행
- `RUN`: 빌드 중에 명령어를 실행합니다.
- `CMD`: 컨테이너가 시작될 때 기본 명령어를 지정합니다.
- `ENTRYPOINT`: 특정 명령어를 강제로 실행합니다.

#### 구성
- `EXPOSE`: 컨테이너 포트를 지정합니다.
- `ENV`: 환경변수를 설정합니다.
- `WORKDIR`: 작업 디렉터리를 설정합니다.
- `USER`: 명령어 실행을 위한 사용자/그룹을 설정합니다.

#### 빌드 프로세스
- `ONBUILD`: 자식 이미지를 위한 명령어를 지정합니다.
- `ARG`: 빌드 시간 변수를 선언합니다.
- `SHELL`: 명령어를 위한 셸을 사용자 정의합니다.

#### 메타데이터
- `LABEL`: 메타데이터(이름, 버전, 저자)를 추가합니다.
- `STOPSIGNAL`: 컨테이너 정지 신호를 사용자 정의합니다.
- `HEALTHCHECK`: 컨테이너 헬스체크 방법을 정의합니다.