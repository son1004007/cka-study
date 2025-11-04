
# 🧠 Kubernetes 기본 구조 (따배쿠 정리)

![Cluster Architecture](screenshot%202025-11-04%20090634.png)

> 이 다이어그램은 Master(Control Plane)와 Node(Worker)의 구성 요소,  
> 그리고 `kubectl create deploy ui --image=nginx --namespace=blue` 명령이  
> 실제로 클러스터 내에서 어떤 흐름으로 동작하는지를 보여줍니다.

---

## 🧩 전체 구성 요약

| 구성 요소 | 위치 | 주요 역할 |
|------------|-------|------------|
| **API Server** | Master | `kubectl` 명령의 입구. 요청 검증 후 etcd에 기록 |
| **etcd 저장소** | Master | 모든 Kubernetes 오브젝트 상태를 저장 (key-value DB) |
| **Scheduler** | Master | 파드를 어느 노드에 배치할지 결정 |
| **Controller Manager** | Master | Deployment / ReplicaSet 상태를 지속적으로 조정 |
| **CoreDNS** | Master (Pod) | 서비스명 → Pod IP 변환 (내부 DNS) |
| **kubelet** | Node | 실제 컨테이너(Pod) 실행 및 상태 보고 |
| **kube-proxy** | Node | Service → Pod 간 트래픽 라우팅 관리 |
| **containerd / docker** | Node | 컨테이너 런타임 (이미지 Pull, 실행) |

---

## 🔁 명령어 흐름 (kubectl → API → Scheduler → Node)

```bash
kubectl create deploy ui --image=nginx --namespace=blue
```

1. **kubectl** → API Server에 요청 전송
2. **API Server** → 요청 검증 후 etcd에 Deployment 오브젝트 저장
3. **Controller** → Deployment를 보고 ReplicaSet 생성
4. **Scheduler** → Pod를 배치할 노드 결정
5. **kubelet(node1, node2)** → 실제 컨테이너 생성
6. **kube-proxy** → Service IP/Port를 통해 트래픽 라우팅
7. **CoreDNS** → `ui.blue.svc.cluster.local` DNS 등록

---

## 🧭 Namespace (blue, orange, green, devel)

| Namespace  | 용도                |
| ---------- | ----------------- |
| **blue**   | 운영(Production) 환경 |
| **orange** | 베타테스트(Beta) 환경    |
| **green**  | 개발(Dev) 환경        |
| **devel**  | 개인 테스트용           |

> 네임스페이스는 하나의 클러스터 안에서 자원을 구획화하는 논리적 단위입니다.
> 각 네임스페이스는 자체적인 Pod, Service, ConfigMap, Secret을 가집니다.

---

## 🧠 기억 포인트

* 모든 명령은 **API Server → etcd → Controller → Scheduler → kubelet** 순서로 동작
* Master는 “지휘관”, Node는 “일꾼”
* kube-proxy는 서비스 트래픽을 Pod로 라우팅
* CoreDNS는 클러스터 내부 DNS 역할
* Namespace는 환경/팀별 격리 단위 (색상으로 시각화 가능)

---

## 📘 핵심 암기 명령

```bash
kubectl get componentstatuses
kubectl get nodes -o wide
kubectl get all -A
kubectl describe pod <pod-name>
kubectl logs -f <pod-name>
```

---

✅ **Tip:**
이 구조가 머릿속에 잡혀 있으면, `kubectl` 명령 하나를 실행할 때
클러스터 내부에서 어떤 일이 일어나는지를 쉽게 그릴 수 있습니다.

