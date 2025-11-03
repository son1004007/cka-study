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
