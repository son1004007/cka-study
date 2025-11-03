# 💾 Storage Guide
> PV/PVC, ConfigMap, Secret, CSI Plugin 구성 및 관리

### 학습 목표
- PersistentVolume / PersistentVolumeClaim 이해
- 동적 프로비저닝 실습
- ConfigMap / Secret 생성 및 Pod에 주입
- CSI 기반 스토리지 연결

### 주요 개념
- PV/PVC: 영구 볼륨 관리
- StorageClass: 동적 스토리지 프로비저닝
- ConfigMap / Secret: 설정 및 민감정보 관리
- AccessModes: RWO, RWX 등 접근 방식

### 시험 포인트
- PVC → Pod 매핑 확인
- Secret을 env와 volume으로 마운트
- StorageClass 자동 생성 확인
