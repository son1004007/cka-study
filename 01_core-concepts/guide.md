# 🧩 Core Concepts Guide
> Kubernetes의 가장 기본이자 핵심 구성요소 이해 (Pod → Deployment → Service → Ingress)

### 학습 목표
- Pod / ReplicaSet / Deployment / Service 구조 완전 이해
- kubectl 주요 명령 숙련 (`get`, `describe`, `logs`, `apply`)
- 실제 YAML 작성 및 롤링 업데이트·롤백 실습

### 주요 개념
- Pod: 컨테이너 실행의 최소 단위
- ReplicaSet: Pod의 개수를 보장
- Deployment: ReplicaSet의 버전 관리
- Service: Pod에 접근하는 네트워크 엔드포인트
- Ingress: HTTP 라우팅과 도메인 기반 접근

### 시험 포인트
- Pod YAML 직접 작성 (`--dry-run=client -o yaml`)
- Deployment 롤링 업데이트 / 롤백
- NodePort / ClusterIP / Ingress 구분 및 설정
