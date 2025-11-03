# 📚 Reference & Resources Guide
> CKA 준비를 위한 공식 문서, 튜토리얼, 툴 모음

### 공식 문서
- [Kubernetes Docs](https://kubernetes.io/docs/)
- [CNCF CKA Exam Curriculum (2025)](https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/)
- [Helm](https://helm.sh/docs/)
- [Gateway API](https://gateway-api.sigs.k8s.io/)

### 실습 도구
- [killer.sh (CKA Mock)](https://killer.sh/)
- [KodeKloud CKA Labs](https://kodekloud.com/)
- [Katacoda Labs (무료 실습)](https://www.katacoda.com/)
- [CKA Exercises by Michael Solomon](https://github.com/mmumshad/kubernetes-the-hard-way-labs)


### 유용한 명령
```bash
kubectl explain pod.spec.containers
kubectl get all -A
kubectl get events --sort-by=.metadata.creationTimestamp | tail
