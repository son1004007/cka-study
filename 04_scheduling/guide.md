# ⚙️ Workloads & Scheduling Guide
> Job, CronJob, Node Affinity, Taints/Tolerations 실습

### 학습 목표
- Job/CronJob을 이용한 배치 작업 생성
- NodeSelector / Affinity / Toleration 이해
- 리소스 요청/제한 설정 (Requests / Limits)

### 주요 개념
- Taint/Toleration: 특정 노드 회피/허용
- Affinity/AntiAffinity: 배치 전략
- HPA: 부하 기반 자동 스케일링
- Job/CronJob: 일회성·주기적 작업 관리

### 시험 포인트
- Job 완료 조건 (`completions`, `backoffLimit`)
- CronJob 주기(`*/5 * * * *`) 설정
- Taint 노드에 파드 스케줄링 제한
