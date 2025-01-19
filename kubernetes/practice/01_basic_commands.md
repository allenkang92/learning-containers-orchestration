# 1. 쿠버네티스 기본 명령어

## 1.1 kubectl 소개

kubectl은 쿠버네티스 클러스터를 제어하기 위한 커맨드라인 도구입니다.

## 1.2 기본 명령어

### 1.2.1 리소스 조회
```bash
# 파드 목록 조회
kubectl get pods

# 서비스 목록 조회
kubectl get services   # 또는 kubectl get svc

# 디플로이먼트 목록 조회
kubectl get deployments

# 모든 리소스 조회
kubectl get all
```

### 1.2.2 리소스 상세 정보
```bash
# 파드 상세 정보
kubectl describe pod [파드이름]

# 서비스 상세 정보
kubectl describe service [서비스이름]

# 디플로이먼트 상세 정보
kubectl describe deployment [디플로이먼트이름]
```

### 1.2.3 로그 확인
```bash
# 파드 로그 확인
kubectl logs [파드이름]

# 실시간 로그 확인
kubectl logs -f [파드이름]
```

## 1.3 리소스 관리 명령어

### 1.3.1 리소스 생성
```bash
# YAML 파일로부터 리소스 생성
kubectl apply -f [파일명.yml]

# 명령어로 직접 리소스 생성
kubectl create deployment [이름] --image=[이미지명]
```

### 1.3.2 리소스 삭제
```bash
# 특정 리소스 삭제
kubectl delete pod [파드이름]
kubectl delete service [서비스이름]
kubectl delete deployment [디플로이먼트이름]

# YAML 파일에 정의된 리소스 삭제
kubectl delete -f [파일명.yml]
```

### 1.3.3 스케일링
```bash
# 디플로이먼트 스케일 조정
kubectl scale deployment [디플로이먼트이름] --replicas=[숫자]
```
