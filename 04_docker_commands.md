# 도커 명령어

## 1. 도커 명령어의 기본

### 1.1. 기본 구조

컨테이너를 다루는 모든 명령은 `docker`로 시작하며, 기본적인 형태는 다음과 같습니다.

docker [커맨드] [대상] [옵션] [인자]

* **커맨드:** 수행할 동작 (예: `run`, `start`, `stop`)
* **대상:** 동작의 대상 (예: 컨테이너 이름, 이미지 이름)
* **옵션:** 커맨드의 세부 설정 (예: `-d`, `--name`)
* **인자:** 대상에 전달할 값 (특정 커맨드에서 사용)

### 1.2. 커맨드의 구성

커맨드는 상위 커맨드와 하위 커맨드로 구성될 수 있습니다. 상위 커맨드는 대상의 종류를, 하위 커맨드는 수행할 동작을 나타냅니다.

docker 상위_커맨드 하위_커맨드 [옵션] [대상]

예시: docker container start my_container

### 1.3. 옵션

옵션은 커맨드의 동작 방식을 세밀하게 조정합니다.

* `-` 또는 `--`로 시작합니다.
* 커맨드에 따라 사용 가능한 옵션이 다릅니다.
* 짧은 옵션(예: `-d`)은 여러 개를 묶어서 사용할 수 있습니다 (예: `-dit`).
* `--이름=값` 형태로 값을 지정하는 옵션도 있습니다.

### 1.4. 대상

대상은 커맨드가 적용될 구체적인 이름(예: 컨테이너 이름, 이미지 이름)을 나타냅니다.

### 1.5. 인자

인자는 대상에 전달될 값으로, 주로 문자 코드나 포트 번호 등을 지정합니다. 사용 빈도는 높지 않습니다.

## 2. 주요 도커 명령어

### 2.1. 도커 버전 확인
docker version

도커 엔진과 명령행 도구의 버전을 확인합니다.

### 2.2. 컨테이너 조작 관련 커맨드 (`docker container`)

컨테이너의 생성, 실행, 중지, 삭제 등 컨테이너 관리에 사용되는 명령어입니다.

| 하위 커맨드 | 설명 | 주요 옵션 | 예시 |
|:--|:--|:--|:--|
| `start` | 정지된 컨테이너를 실행 | `-i` | `docker container start my_container` |
| `stop` | 실행 중인 컨테이너를 정지 | `-t` | `docker container stop my_container` |
| `create` | 이미지를 기반으로 새 컨테이너 생성 (실행은 하지 않음) | `--name`, `-e`, `-p`, `-v` | `docker container create --name my_container ubuntu` |
| `run` | 이미지를 다운로드하고 컨테이너를 생성 및 실행 (`pull`, `create`, `start` 합침) | `--name`, `-e`, `-p`, `-v`, `-d`, `-i`, `-t` | `docker container run -d -p 8080:80 nginx` |
| `rm` | 정지된 컨테이너를 삭제 | `-f`, `-v` | `docker container rm my_container` |
| `exec` | 실행 중인 컨테이너 내부에서 명령어 실행 | `-i`, `-t` | `docker container exec -it my_container bash` |
| `ls` | 컨테이너 목록 출력 | `-a` (모든 컨테이너), `-q` (ID만 출력) | `docker container ls -a` |
| `cp` | 컨테이너와 호스트 간 파일 복사 | | `docker container cp my_container:/app/data ./` |
| `commit` | 컨테이너의 변경 사항을 새로운 이미지로 저장 | | `docker container commit my_container my_image` |

### 2.3. 이미지 조작 관련 커맨드 (`docker image`)

이미지의 다운로드, 검색, 삭제 등 이미지 관리에 사용되는 명령어입니다.

| 하위 커맨드 | 설명 | 주요 옵션 | 예시 |
|:--|:--|:--|:--|
| `pull` | 레지스트리에서 이미지 다운로드 | | `docker image pull ubuntu:latest` |
| `rm` | 로컬 이미지 삭제 | `-f` | `docker image rm my_image` |
| `ls` | 로컬 이미지 목록 출력 | `-a` | `docker image ls` |
| `build` | Dockerfile을 기반으로 이미지 빌드 | `-t` | `docker image build -t my_image .` |
| `search` | 도커 허브에서 이미지 검색 | | `docker image search nginx` |

### 2.4. 볼륨 조작 관련 커맨드 (`docker volume`)

컨테이너의 영구적인 데이터 저장을 위한 볼륨 관리에 사용되는 명령어입니다.

| 하위 커맨드 | 설명 | 주요 옵션 | 예시 |
|:--|:--|:--|:--|
| `create` | 볼륨 생성 | `--name` | `docker volume create my_volume` |
| `inspect` | 볼륨 상세 정보 출력 | | `docker volume inspect my_volume` |
| `ls` | 볼륨 목록 출력 | | `docker volume ls` |
| `prune` | 사용하지 않는 볼륨 일괄 삭제 | | `docker volume prune` |
| `rm` | 특정 볼륨 삭제 | | `docker volume rm my_volume` |

### 2.5. 네트워크 조작 관련 커맨드 (`docker network`)

도커 컨테이너 간의 통신을 위한 네트워크 관리에 사용되는 명령어입니다.

| 하위 커맨드 | 설명 | 주요 옵션 | 예시 |
|:--|:--|:--|:--|
| `connect` | 컨테이너를 네트워크에 연결 | | `docker network connect my_network my_container` |
| `disconnect` | 컨테이너를 네트워크에서 연결 해제 | | `docker network disconnect my_network my_container` |
| `create` | 새로운 네트워크 생성 | `--driver` | `docker network create my_network` |
| `inspect` | 네트워크 상세 정보 출력 | | `docker network inspect my_network` |
| `ls` | 네트워크 목록 출력 | | `docker network ls` |
| `prune` | 사용하지 않는 네트워크 일괄 삭제 | | `docker network prune` |
| `rm` | 특정 네트워크 삭제 | | `docker network rm my_network` |

### 2.6. 컨테이너 오케스트레이션 관련 커맨드

도커 스웜과 같은 컨테이너 오케스트레이션 환경에서 사용되는 명령어입니다.

| 커맨드 | 설명 |
|:--|:--|
| `checkpoint` | 컨테이너의 현재 상태를 저장하고 복원합니다. |
| `node` | 도커 스웜 노드를 관리합니다. |
| `plugin` | 도커 플러그인을 관리합니다. |
| `secret` | 도커 스웜에서 비밀 정보를 관리합니다. |
| `service` | 도커 스웜 서비스를 관리합니다. |
| `stack` | 여러 서비스를 묶은 스택을 관리합니다 (도커 스웜 또는 쿠버네티스). |
| `swarm` | 도커 스웜을 초기화하거나 관리합니다. |
| `system` | 도커 엔진의 시스템 정보를 확인합니다. |

### 2.7. 도커 허브 관련 커맨드

도커 이미지 레지스트리인 도커 허브와 상호작용하기 위한 명령어입니다.

| 커맨드 | 설명 | 주요 옵션 | 예시 |
|:--|:--|:--|:--|
| `login` | 도커 레지스트리에 로그인 | `-u`, `-p` | `docker login -u myuser` |
| `logout` | 도커 레지스트리에서 로그아웃 | | `docker logout` |
| `search` | 도커 레지스트리에서 이미지 검색 | | `docker search ubuntu` |