# 3. 서비스와 네트워킹 실습

## 3.1 서비스 타입

### 3.1.1 ClusterIP 서비스
```bash
# ClusterIP 서비스 생성
kubectl apply -f examples/apache_service.yml

# 서비스 확인
kubectl get services
```

### 3.1.2 NodePort 서비스
```yaml
# nodeport_service.yml 예시
apiVersion: v1
kind: Service
metadata:
  name: apache-nodeport
spec:
  type: NodePort
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30080
  selector:
    app: apachekube
```

## 3.2 서비스 디버깅

### 3.2.1 서비스 연결 테스트
```bash
# 서비스 엔드포인트 확인
kubectl get endpoints

# 서비스 상세 정보 확인
kubectl describe service [서비스이름]
```

### 3.2.2 네트워크 테스트
```bash
# 임시 디버깅 파드 생성
kubectl run test-pod --image=busybox -it --rm -- wget -O- [서비스이름]:[포트]
```

## 3.3 로드 밸런싱 테스트

### 3.3.1 부하 테스트
```bash
# 여러 요청 보내기
for i in {1..10}; do kubectl run test-$i --image=busybox -it --rm -- wget -O- [서비스이름]:[포트]; done
```

### 3.3.2 로그 분석
```bash
# 각 파드의 접근 로그 확인
kubectl logs -l app=apachekube
```
