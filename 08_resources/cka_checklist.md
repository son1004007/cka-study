# CKA 체크리스트

## Cluster / Install / Config
- [ ] kubeadm init/join/reset
- [ ] Control-plane 구성요소 개념
- [ ] CNI 적용(flannel/calico)
- [ ] etcd 스냅샷 save/restore

## Workloads & Scheduling
- [ ] Pod/RS/Deployment
- [ ] Job/CronJob
- [ ] Label/Selector
- [ ] Taint/Toleration, Affinity
- [ ] Requests/Limits, HPA

## Services & Networking
- [ ] ClusterIP / NodePort / LoadBalancer
- [ ] Ingress Controller
- [ ] CoreDNS, kube-proxy
- [ ] NetworkPolicy (deny-all → 허용)

## Storage & Config
- [ ] PV/PVC/StorageClass
- [ ] emptyDir/hostPath 이해
- [ ] ConfigMap/Secret (env/volume)

## Security & RBAC
- [ ] ServiceAccount
- [ ] Role/ClusterRole, RoleBinding
- [ ] PodSecurityContext (runAsUser, fsGroup)

## Troubleshooting
- [ ] logs/describe/debug
- [ ] CrashLoop 원인 분석
- [ ] Node NotReady 복구(kubelet)
- [ ] etcd 백업/복구 실습
