# 2. 디플로이먼트 실습

## 2.1 Apache 웹 서버 배포

### 2.1.1 디플로이먼트 생성
```bash
# apache_deployment.yml 파일 적용
kubectl apply -f examples/apache_deployment.yml

# 파드 생성 확인
kubectl get pods

# 디플로이먼트 상태 확인
kubectl get deployments
```

### 2.1.2 서비스 생성
```bash
# apache_service.yml 파일 적용
kubectl apply -f examples/apache_service.yml

# 서비스 생성 확인
kubectl get services
```

## 2.2 디플로이먼트 관리

### 2.2.1 스케일링
```bash
# 레플리카 수 조정
kubectl scale deployment apachedep --replicas=5

# 변경 사항 확인
kubectl get pods
```

### 2.2.2 롤링 업데이트
```bash
# 이미지 업데이트
kubectl set image deployment/apachedep apachekubene=nginx

# 업데이트 상태 확인
kubectl rollout status deployment/apachedep
```

### 2.2.3 롤백
```bash
# 이전 버전으로 롤백
kubectl rollout undo deployment/apachedep

# 롤백 상태 확인
kubectl rollout status deployment/apachedep
```

## 2.3 문제 해결

### 2.3.1 로그 확인
```bash
# 특정 파드의 로그 확인
kubectl logs [파드이름]
```

### 2.3.2 디버깅
```bash
# 파드 상세 정보 확인
kubectl describe pod [파드이름]

# 파드 내부 접속
kubectl exec -it [파드이름] -- /bin/bash
```
