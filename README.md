# CKA Study Repository

- 환경: Master 1 (Rocky 9.6, K8s v1.29.15, containerd) + Worker 3
- 목적: **CKA 취득**을 위한 실습/노트/스크립트 **버전관리**
- 운영: 모든 실습은 `~/cka-study`에 기록하고 **매일 푸시** (`gsave` 단축 사용)

## 📆 진행 현황
| 주차 | 주제 | 상태 |
|---|---|---|
| 1 | Core Concepts (Pod/Deployment/Service) | ☐ |
| 2 | Workloads & Scheduling | ☐ |
| 3 | Services & Networking | ☐ |
| 4 | Storage / Config / Secret | ☐ |
| 5 | Security & RBAC | ☐ |
| 6 | Troubleshooting | ☐ |
| 7 | Mock Tests & 약점보완 | ☐ |
| 8 | 실전 대비 정리 | ☐ |

- 체크 방법: 각 주차 노트 파일에서 `- [x]` 로 진행 체크 후 `gsave`로 커밋/푸시.

## 자동완성 설정
sudo dnf install -y bash-completion
source /etc/profile.d/bash_completion.sh
source <(kubectl completion bash)
echo 'source <(kubectl completion bash)' >> ~/.bashrc


## 🧭 CKA 2025 개편 반영 목차

> 📅 2025년 2월 기준 최신 개정 반영  
> 출처: [CNCF / Linux Foundation 공식 가이드](https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/)  
> (Helm · Kustomize · Gateway API · CRD/Operator 추가 포함)

---

### 🏗️ 1. Cluster Architecture, Installation & Configuration (25%)

- 클러스터 설계 및 설치 (`kubeadm`, `kubelet`, 컨트롤플레인 구조)
- CNI · CRI · CSI 확장 인터페이스 이해 및 설정
- 고가용성(HA) 및 스케일링 고려 구성
- **Helm / Kustomize**를 이용한 리소스 배포 및 관리
- **CRD(CustomResourceDefinition)** 및 **Operator 패턴** 개념 포함
- etcd 스냅샷 생성/복원, Control Plane 유지보수

---

### ⚙️ 2. Workloads & Scheduling (15%)

- Pod / ReplicaSet / Deployment / DaemonSet / StatefulSet
- Job / CronJob / InitContainer
- Labels · Selectors를 통한 파드 그룹 관리
- Node Affinity / Anti-Affinity , Taints/Tolerations
- Resource Requests / Limits, HPA (오토스케일링)
- Admission Controller, 스케줄링 정책 및 큐 관리

---

### 🌐 3. Services & Networking (20%)

- Service 타입: ClusterIP / NodePort / LoadBalancer
- **Ingress Controller** 및 **Gateway API**를 통한 외부 라우팅
- CoreDNS 및 kube-proxy 동작 원리
- NetworkPolicy 작성으로 Pod 간 통신 제어
- 네트워크 트러블슈팅 (`describe`, `logs`, `tcpdump`, `nslookup`)

---

### 💾 4. Storage (10%)

- PersistentVolume / PersistentVolumeClaim / StorageClass
- 동적 프로비저닝과 AccessModes(`ReadWriteOnce`, `ReadOnlyMany` 등)
- **ConfigMap / Secret** : 환경변수 및 볼륨 주입
- CSI 기반 스토리지 플러그인 관리

---

### 🧰 5. Troubleshooting (30%)

- Pod CrashLoopBackOff / ImagePull / Pending 문제 분석
- Node NotReady / kubelet 오류 복구
- Control-plane 컴포넌트 (etcd · scheduler · controller-manager) 상태 점검
- 로그 / 이벤트 / 리소스 관계 조사를 통한 문제 해결
- etcd 스냅샷 저장 및 복구 (마스터 노드)
- 네트워크 · 스토리지 · RBAC 문제 트러블슈팅

---

### 📘 참고 / 업데이트 메모

- ✅ **Helm 및 Kustomize** 가 새롭게 포함되어 패키지형 리소스 관리 능력을 요구  
- ✅ **Gateway API** 및 **CRD/Operator** 항목이 추가되어 확장성 주제 강조  
- ✅ 단순 명령어 암기보다는 **운영·복구 능력** 평가 비중 증가  
- 🧾 공식 출제 비율 (2025-02 기준):   
  Cluster 25 % · Workloads 15 % · Networking 20 % · Storage 10 % · Troubleshooting 30 %

---
