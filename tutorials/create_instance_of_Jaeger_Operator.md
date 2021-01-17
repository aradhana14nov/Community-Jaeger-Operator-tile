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
  name: jaeger
EOF
```

**Step 2:** create Jaeger Operator instance in the namespace "operators"

```execute
kubectl create -f jaegerInstance.yaml 
```

You will see the following output:

```
jaeger.jaegertracing.io/jaeger created
```

Check the Pods status:

```execute
kubectl get pods
```

You will see similar to this output:

```
NAME                          READY   STATUS    RESTARTS   AGE
pod/jaeger-788f55ddc9-2cj4n   1/1     Running   0          19s
```

Check all the kubernetes resources:

```execute
kubectl get all
```


You will see similar to this output:

```
NAME                          READY   STATUS    RESTARTS   AGE
pod/jaeger-788f55ddc9-2cj4n   1/1     Running   0          19s

NAME                                TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                                  AGE
service/jaeger-agent                ClusterIP   None            <none>        5775/UDP,5778/TCP,6831/UDP,6832/UDP      19s
service/jaeger-collector            ClusterIP   10.111.142.2    <none>        9411/TCP,14250/TCP,14267/TCP,14268/TCP   19s
service/jaeger-collector-headless   ClusterIP   None            <none>        9411/TCP,14250/TCP,14267/TCP,14268/TCP   19s
service/jaeger-query                ClusterIP   10.109.253.83   <none>        16686/TCP                                19s
service/kubernetes                  ClusterIP   10.96.0.1       <none>        443/TCP                                  126m

NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/jaeger   1/1     1            1           19s

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/jaeger-788f55ddc9   1         1         1       19s
```
