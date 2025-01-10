# 2. 도커 이미지와 컨테이너

## 2.1 도커 이미지

### 2.1.1 이미지 개념
- 컨테이너 실행에 필요한 파일과 설정값 등을 포함
- 상태값을 가지지 않고 변하지 않음 (Immutable)
- 계층화된 파일 시스템 구조

### 2.1.2 이미지 구성
- 베이스 이미지
- 추가 레이어
- 이미지 설정 정보

### 2.1.3 이미지 태그
- 이미지 버전 관리
- 태그 명명 규칙
- Latest 태그 사용

## 2.2 도커 컨테이너

### 2.2.1 컨테이너 개념
- 이미지를 실행한 상태
- 격리된 실행 환경
- 프로세스 단위의 격리

### 2.2.2 컨테이너 특징
- 독립적인 파일시스템
- 호스트와 자원 공유
- 네트워크 격리
- 프로세스 격리

### 2.2.3 컨테이너 생명주기
- 생성 (Created)
- 실행 (Running)
- 중지 (Stopped)
- 삭제 (Deleted)

## 2.3 이미지와 컨테이너의 관계

### 2.3.1 기본 관계
- 이미지는 컨테이너의 템플릿
- 하나의 이미지로 여러 컨테이너 생성 가능
- 컨테이너의 변경사항은 이미지에 영향 없음

### 2.3.2 데이터 관리
- 컨테이너 레이어
- 볼륨 마운트
- 바인드 마운트

## 2.4 이미지 관리 전략

### 2.4.1 이미지 최적화
- 레이어 최소화
- 멀티스테이지 빌드
- 캐시 활용

### 2.4.2 이미지 보안
- 취약점 스캔
- 최신 버전 유지
- 불필요한 패키지 제거