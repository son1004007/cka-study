# 🔐 Security & RBAC Guide
> Kubernetes 접근 제어와 권한 설정 중심 실습

### 학습 목표
- Role / RoleBinding / ClusterRole 이해
- ServiceAccount를 이용한 인증
- PodSecurityContext 적용 (runAsUser, fsGroup)
- 이미지 풀 시크릿 및 PSP 대체 정책

### 주요 개념
- RBAC: Role-Based Access Control
- SA(ServiceAccount): Pod가 API 서버에 접근 시 사용
- PodSecurityContext: 런타임 보안 설정
- PSP(PodSecurityPolicy) 대체 정책: PodSecurity Standard

### 시험 포인트
- RoleBinding을 특정 SA에 연결
- runAsUser/fsGroup 적용 확인
- API 접근 권한 제한/허용 테스트
