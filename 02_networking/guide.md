# 🌐 Networking Guide
> Service, Ingress, Gateway API, NetworkPolicy 중심의 네트워킹 구성 실습

### 학습 목표
- Pod 간 통신 구조 이해
- Service 타입 (ClusterIP / NodePort / LoadBalancer) 구성
- Ingress Controller와 Gateway API 실습
- NetworkPolicy를 통한 접근제어

### 주요 개념
- kube-proxy: 서비스 트래픽 라우팅 담당
- CoreDNS: 클러스터 내부 DNS 해석
- Ingress: Layer7 트래픽 라우팅
- NetworkPolicy: Pod 간 통신 제어

### 시험 포인트
- NodePort와 ClusterIP 구분
- Ingress YAML 직접 작성
- default-deny + 허용 정책 구현
