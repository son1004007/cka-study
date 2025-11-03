# 🧩 1주차 Core Concepts 집중 학습 가이드 (CKA 2025 단기 플랜)

> 목표: 3~4일 내 **Pod → Deployment → Service → Ingress** 완전 숙련  
> 시험 출제 비중: 약 25% (가장 기본이면서 필수 파트)

---

## 📆 진행 일정 예시

| 일차 | 주제 | 학습 목표 | 실습 파일 |
|------|------|------------|------------|
| Day 1 | Pod / ReplicaSet | Pod 구조 및 생성 원리 이해, ReplicaSet 실습 | `pod.yaml`, `rs.yaml` |
| Day 2 | Deployment | 롤링 업데이트 / 롤백 / 스케일 조정 | `deploy-nginx.yaml` |
| Day 3 | Service / Ingress | 외부 접근 / 라우팅 실습 | `svc-nodeport.yaml`, `ingress.yaml` |
| Day 4 | 정리 및 트러블슈팅 | Describe / Logs / Pod 재시작 테스트 | - |

---

## 🧱 Day 1 — Pod / ReplicaSet

### 🎯 학습 포인트
- Pod 구조 (`apiVersion`, `kind`, `metadata`, `spec`)
- ReplicaSet이 Pod를 자동 관리하는 방식
- Label / Selector의 연결 관계

### 🧠 실습 명령
```bash
# 네임스페이스 생성
kubectl create ns cka-lab
kubectl config set-context --current --namespace=cka-lab

# Pod 생성
kubectl run nginx --image=nginx
kubectl get pods -o wide
kubectl describe pod nginx

# YAML 기반 생성
kubectl run nginx2 --image=nginx --dry-run=client -o yaml > pod.yaml
kubectl apply -f pod.yaml


# ReplicaSet
cat > rs-nginx.yaml <<YAML
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: rs-nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.25
YAML

kubectl apply -f rs-nginx.yaml
kubectl get rs,pods -o wide

```
## 🚀 Day 2 — Deployment
### 🎯 학습 포인트
- Deployment = ReplicaSet 자동 관리자
- 롤링 업데이트 / 롤백 / 스케일 조정 명령 숙지
- 실시간 배포 상태 확인 (kubectl rollout status)

### 🧠 실습 명령
```bash
# Deployment 생성
kubectl create deploy web --image=nginx
kubectl get deploy,rs,pods

# 스케일 조정
kubectl scale deploy web --replicas=5
kubectl get pods -o wide

# 롤링 업데이트
kubectl set image deploy/web nginx=nginx:1.27
kubectl rollout status deploy/web
kubectl rollout history deploy/web

# 롤백
kubectl rollout undo deploy/web
```


## 🌐 Day 3 — Service / Ingress
### 🎯 학습 포인트
- ClusterIP / NodePort 차이
- Ingress Controller로 외부 트래픽 라우팅
- NodePort 접근 테스트 (curl or wget)

### 🧠 실습 명령
```bash
# NodePort Service
kubectl expose deploy web --port=80 --type=NodePort
kubectl get svc web -o wide

# 노드 포트 확인 후 접근
NODEPORT=$(kubectl get svc web -o jsonpath='{.spec.ports[0].nodePort}')
curl http://<WORKER_NODE_IP>:$NODEPORT

# Ingress (nginx ingress controller가 설치되어 있다고 가정)
cat > ingress-web.yaml <<YAML
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web-ing
spec:
  rules:
  - host: web.local
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: web
            port:
              number: 80
YAML

kubectl apply -f ingress-web.yaml
kubectl get ingress
```
## 🔍 Day 4 — 정리 & 트러블슈팅
### 🎯 학습 포인트
- Pod 로그 / Describe / Events
- CrashLoopBackOff 대응
- YAML 편집(kubectl edit) 및 복원(kubectl rollout undo)

### 🧠 실습 명령
```bash
# Pod 상세 점검
kubectl describe pod <pod_name>
kubectl logs <pod_name> | tail -n 5

# Pod 재시작 / 상태 확인
kubectl delete pod <pod_name>
kubectl get pods -w
```
### 🧾 체크리스트
|항목|완료|
|---------------|------|
|Pod 구조를 직접 YAML로 작성했다|	☐|
|ReplicaSet으로 동일 Pod 3개 생성|	☐|
|Deployment 롤링 업데이트 / 롤백 성공|	☐|
|NodePort를 통해 외부 접근 확인|	☐|
|Ingress 설정 후 서비스 정상 접근 확인|	☐|

### 📚 복습 요약 (필수 암기 명령)
```bash
kubectl run nginx --image=nginx
kubectl get po -o wide
kubectl create deploy web --image=nginx
kubectl scale deploy web --replicas=5
kubectl expose deploy web --port=80 --type=NodePort
kubectl rollout undo deploy web
kubectl get all -A
kubectl describe pod <pod>
kubectl logs -f <pod>
```
