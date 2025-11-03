# Quick Start (하루차 실습용)

## 네임스페이스
kubectl create ns cka-lab
kubectl config set-context --current --namespace=cka-lab

[200~
## Deployment & Service 샘플
cat > deploy-nginx.yaml <<YAML
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: nginx
        image: nginx:1.25
        ports:
        - containerPort: 80
YAML

cat > svc-web-nodeport.yaml <<YAML
apiVersion: v1
kind: Service
metadata:
  name: web-svc
spec:
  selector:
    app: web
  type: NodePort
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30080
YAML

kubectl apply -f deploy-nginx.yaml
kubectl apply -f svc-web-nodeport.yaml
kubectl get deploy,po,svc -o wide
