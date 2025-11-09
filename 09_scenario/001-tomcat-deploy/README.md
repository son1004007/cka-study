# 🧩 Scenario 06 - Tomcat Deployment & WAR 배포 (iiac-viz)

> 목표: Kubernetes 환경에서 Tomcat 10을 배포하고, WAR 파일을 Pod 내부로 복사하여 실제 웹 서비스가 정상 동작함을 확인한다.

---

## 1️⃣ 시나리오 개요

1. 네임스페이스 `iiac-viz` 생성  
2. Tomcat 10 Deployment/Service 생성 (`NodePort 30080 → 8080`)  
3. Pod 부팅 확인 후 `ROOT.war` 원격 복사  
4. Tomcat이 자동으로 WAR 전개(Deploy) → `/` 응답 확인  
5. NodePort/포트포워딩으로 외부/로컬 접속 확인  
6. 문제 시 `logs` / `describe` / `curl` 로 원인 진단 및 복구  

---

## 2️⃣ 환경 정보
| 항목 | 값 |
|------|----|
| OS | Rocky Linux 9.6 |
| K8s 버전 | v1.29.x |
| CNI | Flannel |
| 컨테이너 런타임 | containerd |
| 이미지 | `tomcat:10.1.48-jdk17` |
| 네임스페이스 | `iiac-viz` |
| NodePort | `30080` |

---

## 3️⃣ Deployment / Service 생성


