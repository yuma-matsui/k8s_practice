# k8s Practice

Kubernetes のマニフェストを手元で試すための練習用リポジトリです。  
`manifests/` 配下の YAML を `kubectl apply` して、Pod / Service / Job / CronJob / PV/PVC などの基本リソースの挙動を確認できます。

## 使い方

### 1. 前提

- Kubernetes クラスタに接続できること（例: minikube, kind, Docker Desktop Kubernetes）
- `kubectl` がインストール済みであること

### 2. マニフェストを適用する

```bash
kubectl apply -f manifests/
```

個別に試したい場合:

```bash
kubectl apply -f manifests/pod-nginx.yaml
```

### 3. 状態確認

```bash
kubectl get pods,svc,deploy,rs,job,cronjob,pv,pvc
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

### 4. 後片付け

```bash
kubectl delete -f manifests/
```

## ディレクトリ構成

```text
.
└── manifests/
    ├── pod-nginx.yaml
    ├── svc.yaml
    ├── svc-np.yaml
    ├── rs.yaml
    ├── job.yaml
    ├── cronjob.yaml
    ├── pv0001.yaml
    ├── pvc.yaml
    └── ...（その他検証用マニフェスト）
```

## メモ

- 一部マニフェストは StorageClass や NodePort など、クラスタ設定に依存します。
- うまく動かない場合は `kubectl describe` と `kubectl events --for <resource>` で原因を確認してください。

---
最終更新テスト: Cursor CLI 設定確認用の追記です。
