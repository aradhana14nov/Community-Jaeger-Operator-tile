---
title: Jaeger Operator Tutorial to create an instance of Jaeger Operator
description: This tutorial explains how to create an instance of Jaeger Operator
---

### Create Instance of Jaeger Operator

Jaeger Operator Instance can be created using the Custom Resource Definition YAML files.

**step 1:** Create a custom resource YAML file

```execute
cat <<'EOF' >jaegerInstance.yaml 
apiVersion: jaegertracing.io/v1
kind: Jaeger
metadata:
  name: jaeger-all-in-one-inmemory
EOF
```

**Step 2:** create Jaeger Operator instance in the namespace "operators"

```execute
kubectl create -f jaegerInstance.yaml -n operators
```

You will see the following output:

```
jaeger.jaegertracing.io/jaeger-all-in-one-inmemory created
```

Check the Pods status:

```execute
kubectl get pods -n operators
```

You will see similar to this output:

```
NAME                                         READY   STATUS    RESTARTS   AGE
jaeger-all-in-one-inmemory-d98868849-gd5zv   1/1     Running   0          3m39s
jaeger-operator-76bdc75548-n8r6n             1/1     Running   0          11m
```

Check all the kubernetes resources:

```execute
kubectl get all -n operators
```


You will see similar to this output:

```
NAME                                             READY   STATUS    RESTARTS   AGE
pod/jaeger-all-in-one-inmemory-d98868849-gd5zv   1/1     Running   0          10s
pod/jaeger-operator-76bdc75548-n8r6n             1/1     Running   0          8m16s

NAME                                                    TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                                  AGE
service/jaeger-all-in-one-inmemory-agent                ClusterIP   None            <none>        5775/UDP,5778/TCP,6831/UDP,6832/UDP      10s
service/jaeger-all-in-one-inmemory-collector            ClusterIP   10.104.52.124   <none>        9411/TCP,14250/TCP,14267/TCP,14268/TCP   10s
service/jaeger-all-in-one-inmemory-collector-headless   ClusterIP   None            <none>        9411/TCP,14250/TCP,14267/TCP,14268/TCP   10s
service/jaeger-all-in-one-inmemory-query                ClusterIP   10.96.225.160   <none>        16686/TCP                                10s
service/jaeger-operator-metrics                         ClusterIP   10.110.183.94   <none>        8383/TCP,8686/TCP                        8m5s

NAME                                         READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/jaeger-all-in-one-inmemory   1/1     1            1           10s
deployment.apps/jaeger-operator              1/1     1            1           8m16s

NAME                                                   DESIRED   CURRENT   READY   AGE
replicaset.apps/jaeger-all-in-one-inmemory-d98868849   1         1         1       10s
replicaset.apps/jaeger-operator-76bdc75548             1         1         1       8m16s
```