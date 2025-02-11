# 3. 도커 컨테이너 수정

## 3.1 컨테이너 개조 방법
컨테이너를 개조하는 방법은 두 가지가 있다.
1. 파일 복사와 마운트를 이용한 방법
2. 컨테이너 내부에서 리눅스 명령어를 실행하는 방법

## 3.2 컨테이너에서 셸 사용

### 3.2.1 셸 요구 사항
- 셸은 리눅스 명령어를 실행하기 위해 필요하다
- 대부분의 컨테이너는 `/bin/bash`를 기본 셸로 사용한다

### 3.2.2 셸 접근 명령어

#### 3.2.2.1 실행 중인 컨테이너에 대한 명령어
```bash
docker exec (옵션) 컨테이너_이름 /bin/bash
```

#### 3.2.2.2 새로운 컨테이너에 대한 명령어
```bash
docker run (옵션) 이미지_이름 /bin/bash
```

### 3.2.3 중요 사항
- 컨테이너 셸 내부에서는 도커 명령어를 사용할 수 없다
- `exit` 명령어를 사용하여 호스트 셸로 돌아가야 한다
- 셸 수정 후 컨테이너를 재시작해야 한다

## 3.3 명령어 실행 영역

### 3.3.1 도커 엔진 명령어
도커 엔진을 통해야 하는 명령어:
- 도커 엔진 시작/종료
- 컨테이너 생명주기 관리
- 컨테이너 시작/종료
- 컨테이너와 호스트 간 파일 복사
- 네트워크 설정
- 디스크 설정
- 컨테이너 목록

### 3.3.2 컨테이너 셸 명령어
컨테이너 내부에서 실행하는 명령어:
- 소프트웨어 설치
- 소프트웨어 시작/종료
- 설정 변경
- 컨테이너 내부 파일 작업