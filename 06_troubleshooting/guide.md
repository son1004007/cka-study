# 🧰 Troubleshooting Guide
> 문제 발생 시 빠르게 원인 파악 및 복원하는 능력

### 학습 목표
- Pod CrashLoopBackOff 원인 분석
- Node NotReady / kubelet 중단 복구
- etcd 백업/복원
- 네트워크 및 스토리지 문제 점검

### 주요 개념
- logs / describe / events 분석
- systemctl / journalctl을 이용한 kubelet 점검
- etcdctl snapshot save / restore 명령

### 시험 포인트
- CrashLoopBackOff Pod 분석 및 수정
- Node NotReady 복구 (kubelet 재시작)
- etcd 스냅샷 백업/복원 성공
