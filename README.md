# Deploy Prefect3 on Kubernetes

Refer to: https://github.com/PrefectHQ/prefect-helm

## Install Prefect3's Helm Repo

```
helm repo add prefect https://prefecthq.github.io/prefect-helm
```

## Deploy Server

```
helm -n research-eng-hf uninstall prefect-server
helm -n research-eng-hf install prefect-server prefect/prefect-server -f server-values.yaml
```

## Deploy Worker

```
helm -n research-eng-hf uninstall prefect-worker
helm -n research-eng-hf install prefect-worker prefect/prefect-worker -f worker-values.yaml --set-file worker.config.baseJobTemplate.configuration=base-job-template.json
```

## Deploy RayCluster

```
kubectl delete -f cluster-prefect.yaml
kubectl apply -f cluster-prefect.yaml
```
