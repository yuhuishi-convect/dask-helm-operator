
# Dask Helm Operator 

This repository contains an operator to manage the lifecycle of Dask clusters. 
It is a wrapper using [Operator SDK](https://sdk.operatorframework.io/) around [dask helm charts](https://github.com/dask/helm-chart).


## Installation with make

Prerequisites
* go 
* make 
* kustomize

```
make install deploy
```


## Installation with OLM

TODO

## Start a cluster

The below code starts a cluster with 2 workers + 1 scheduler, and a jupyter notebook server. 

```bash
k apply -f - << EOF
apiVersion: charts.dask.org/v1alpha1
kind: Dask
metadata:
  name: dask-sample
spec:
  # Default values copied from <project_dir>/helm-charts/dask/values.yaml
  jupyter:
    enabled: true
    image:
      repository: daskdev/dask-notebook
      tag: 2021.12.0
    name: jupyter
    password: sha1:aae8550c0a44:9507d45e087d5ee481a5ce9f4f16f37a0867318c
    rbac: true
    replicas: 1
    serviceType: ClusterIP
  scheduler:
    enabled: true
    image:
      repository: daskdev/dask
      tag: 2021.12.0
    name: scheduler
    replicas: 1
    servicePort: 8786
    serviceType: ClusterIP
  worker:
    image:
      dask_worker: dask-worker
      repository: daskdev/dask
      tag: 2021.12.0
    name: worker
    replicas: 2
EOF
```

To clean up, 

```bash
kubectl delete dask dask-sample
```

For a comprehensive on the configs available, please refer to dask helm chart's [`value.yaml`](https://github.com/dask/helm-chart/blob/main/dask/values.yaml)

## Contribution guide

To contribute, download operator-sdk.



