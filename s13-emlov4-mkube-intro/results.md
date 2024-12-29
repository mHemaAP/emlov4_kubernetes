#### Deployment

##### Describe the Deployment - Command
```
kubectl describe deployment classifier-deployment
```

##### Describe the Deployment - Output


```
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl describe deployment classifier-deployment
Name:                   classifier-deployment
Namespace:              default
CreationTimestamp:      Wed, 25 Dec 2024 20:43:37 +0000
Labels:                 app=classifier
Annotations:            deployment.kubernetes.io/revision: 1
Selector:               app=classifier
Replicas:               2 desired | 2 updated | 2 total | 2 available | 0 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:  app=classifier
  Containers:
   classifier:
    Image:         muthukamalan/classifier-k8s
    Port:          8080/TCP
    Host Port:     0/TCP
    Environment:   <none>
    Mounts:        <none>
  Volumes:         <none>
  Node-Selectors:  <none>
  Tolerations:     <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Available      True    MinimumReplicasAvailable
  Progressing    True    NewReplicaSetAvailable
OldReplicaSets:  <none>
NewReplicaSet:   classifier-deployment-88794f4bf (2/2 replicas created)
Events:
  Type    Reason             Age   From                   Message
  ----    ------             ----  ----                   -------
  Normal  ScalingReplicaSet  11m   deployment-controller  Scaled up replica set classifier-deployment-88794f4bf to 2
```


##### Describe the Pod1 - Command

```
mkubectl describe pod classifier-deployment-88794f4bf-c4cdt
```

##### Describe the Pod1 - Output


```
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl describe pod classifier-deployment-88794f4bf-c4cdt
Name:             classifier-deployment-88794f4bf-c4cdt
Namespace:        default
Priority:         0
Service Account:  default
Node:             minikube/192.168.49.2
Start Time:       Wed, 25 Dec 2024 20:43:37 +0000
Labels:           app=classifier
                  pod-template-hash=88794f4bf
Annotations:      <none>
Status:           Running
IP:               10.244.0.10
IPs:
  IP:           10.244.0.10
Controlled By:  ReplicaSet/classifier-deployment-88794f4bf
Containers:
  classifier:
    Container ID:   docker://0c17862d036fbcb56cf78f8505a79d174175061d197a1a838317a6fc98e2fe93
    Image:          muthukamalan/classifier-k8s
    Image ID:       docker-pullable://muthukamalan/classifier-k8s@sha256:6ed53db9268c9eec1ffac6e6221c6c188ed08bcc2e4ec2568c9f990627bd147f
    Port:           8080/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Wed, 25 Dec 2024 20:44:03 +0000
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-sz6qj (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       True 
  ContainersReady             True 
  PodScheduled                True 
Volumes:
  kube-api-access-sz6qj:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  15m   default-scheduler  Successfully assigned default/classifier-deployment-88794f4bf-c4cdt to minikube
  Normal  Pulling    15m   kubelet            Pulling image "muthukamalan/classifier-k8s"
  Normal  Pulled     14m   kubelet            Successfully pulled image "muthukamalan/classifier-k8s" in 1.784s (24.494s including waiting). Image size: 642527004 bytes.
  Normal  Created    14m   kubelet            Created container classifier
  Normal  Started    14m   kubelet            Started container classifier
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$
```

##### Describe the Pod2 - Command

```
mkubectl describe pod classifier-deployment-88794f4bf-np8ml
```

##### Describe the Pod2 - Output

```
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl describe pod classifier-deployment-88794f4bf-np8ml
Name:             classifier-deployment-88794f4bf-np8ml
Namespace:        default
Priority:         0
Service Account:  default
Node:             minikube/192.168.49.2
Start Time:       Wed, 25 Dec 2024 20:43:37 +0000
Labels:           app=classifier
                  pod-template-hash=88794f4bf
Annotations:      <none>
Status:           Running
IP:               10.244.0.9
IPs:
  IP:           10.244.0.9
Controlled By:  ReplicaSet/classifier-deployment-88794f4bf
Containers:
  classifier:
    Container ID:   docker://797d3e2650d662a734207e72e848c1f7fccabd4dfc01fb7b13d6f7961636f72c
    Image:          muthukamalan/classifier-k8s
    Image ID:       docker-pullable://muthukamalan/classifier-k8s@sha256:6ed53db9268c9eec1ffac6e6221c6c188ed08bcc2e4ec2568c9f990627bd147f
    Port:           8080/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Wed, 25 Dec 2024 20:44:01 +0000
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-x8ppg (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       True 
  ContainersReady             True 
  PodScheduled                True 
Volumes:
  kube-api-access-x8ppg:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  17m   default-scheduler  Successfully assigned default/classifier-deployment-88794f4bf-np8ml to minikube
  Normal  Pulling    17m   kubelet            Pulling image "muthukamalan/classifier-k8s"
  Normal  Pulled     17m   kubelet            Successfully pulled image "muthukamalan/classifier-k8s" in 22.769s (22.769s including waiting). Image size: 642527004 bytes.
  Normal  Created    17m   kubelet            Created container classifier
  Normal  Started    17m   kubelet            Started container classifier
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$
```

##### Get the Ingress Details - Command

```
mkubectl get ingress
```

##### Get the Ingress Details - Output

```
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl get ingress
NAME                 CLASS   HOSTS             ADDRESS        PORTS   AGE
classifier-ingress   nginx   earth.localhost   192.168.49.2   80      18m
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl describe ingress classifier-ingress
Name:             classifier-ingress
Labels:           <none>
Namespace:        default
Address:          192.168.49.2
Ingress Class:    nginx
Default backend:  <default>
Rules:
  Host             Path  Backends
  ----             ----  --------
  earth.localhost  
                   /   classifier-service:80 (10.244.0.9:8080,10.244.0.10:8080)
Annotations:       kubernetes.io/ingress.class: nginx
Events:
  Type    Reason  Age                From                      Message
  ----    ------  ----               ----                      -------
  Normal  Sync    17m (x2 over 18m)  nginx-ingress-controller  Scheduled for sync
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$
```

##### Resource Usage - Pods - Command

```
mkubectl top pods
```

##### Resource Usage - Pods - Output

```
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl top pod
NAME                                    CPU(cores)   MEMORY(bytes)   
classifier-deployment-88794f4bf-c4cdt   2m           60Mi            
classifier-deployment-88794f4bf-np8ml   2m           61Mi            
```

##### Resource Usage - Nodes - Command

```
mkubectl top node
```

##### Resource Usage - Nodes - Output

```
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl top node
NAME       CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%   
minikube   144m         7%     1239Mi          32%        
```
##### Cluster State - Command

```
mkubectl get all -o yamls
```

##### Cluster State - Output

```
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$ mkubectl get all -o yaml
apiVersion: v1
items:
- apiVersion: v1
  kind: Pod
  metadata:
    creationTimestamp: "2024-12-25T20:43:37Z"
    generateName: classifier-deployment-88794f4bf-
    labels:
      app: classifier
      pod-template-hash: 88794f4bf
    name: classifier-deployment-88794f4bf-c4cdt
    namespace: default
    ownerReferences:
    - apiVersion: apps/v1
      blockOwnerDeletion: true
      controller: true
      kind: ReplicaSet
      name: classifier-deployment-88794f4bf
      uid: 6dfcb104-591d-435d-9fec-45e39df66a1f
    resourceVersion: "1180"
    uid: eb8cd039-60be-4107-b7bb-f52d3f203b58
  spec:
    containers:
    - image: muthukamalan/classifier-k8s
      imagePullPolicy: Always
      name: classifier
      ports:
      - containerPort: 8080
        protocol: TCP
      resources: {}
      terminationMessagePath: /dev/termination-log
      terminationMessagePolicy: File
      volumeMounts:
      - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
        name: kube-api-access-sz6qj
        readOnly: true
    dnsPolicy: ClusterFirst
    enableServiceLinks: true
    nodeName: minikube
    preemptionPolicy: PreemptLowerPriority
    priority: 0
    restartPolicy: Always
    schedulerName: default-scheduler
    securityContext: {}
    serviceAccount: default
    serviceAccountName: default
    terminationGracePeriodSeconds: 30
    tolerations:
    - effect: NoExecute
      key: node.kubernetes.io/not-ready
      operator: Exists
      tolerationSeconds: 300
    - effect: NoExecute
      key: node.kubernetes.io/unreachable
      operator: Exists
      tolerationSeconds: 300
    volumes:
    - name: kube-api-access-sz6qj
      projected:
        defaultMode: 420
        sources:
        - serviceAccountToken:
            expirationSeconds: 3607
            path: token
        - configMap:
            items:
            - key: ca.crt
              path: ca.crt
            name: kube-root-ca.crt
        - downwardAPI:
            items:
            - fieldRef:
                apiVersion: v1
                fieldPath: metadata.namespace
              path: namespace
  status:
    conditions:
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:44:04Z"
      status: "True"
      type: PodReadyToStartContainers
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:43:37Z"
      status: "True"
      type: Initialized
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:44:04Z"
      status: "True"
      type: Ready
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:44:04Z"
      status: "True"
      type: ContainersReady
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:43:37Z"
      status: "True"
      type: PodScheduled
    containerStatuses:
    - containerID: docker://0c17862d036fbcb56cf78f8505a79d174175061d197a1a838317a6fc98e2fe93
      image: muthukamalan/classifier-k8s:latest
      imageID: docker-pullable://muthukamalan/classifier-k8s@sha256:6ed53db9268c9eec1ffac6e6221c6c188ed08bcc2e4ec2568c9f990627bd147f
      lastState: {}
      name: classifier
      ready: true
      restartCount: 0
      started: true
      state:
        running:
          startedAt: "2024-12-25T20:44:03Z"
      volumeMounts:
      - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
        name: kube-api-access-sz6qj
        readOnly: true
        recursiveReadOnly: Disabled
    hostIP: 192.168.49.2
    hostIPs:
    - ip: 192.168.49.2
    phase: Running
    podIP: 10.244.0.10
    podIPs:
    - ip: 10.244.0.10
    qosClass: BestEffort
    startTime: "2024-12-25T20:43:37Z"
- apiVersion: v1
  kind: Pod
  metadata:
    creationTimestamp: "2024-12-25T20:43:37Z"
    generateName: classifier-deployment-88794f4bf-
    labels:
      app: classifier
      pod-template-hash: 88794f4bf
    name: classifier-deployment-88794f4bf-np8ml
    namespace: default
    ownerReferences:
    - apiVersion: apps/v1
      blockOwnerDeletion: true
      controller: true
      kind: ReplicaSet
      name: classifier-deployment-88794f4bf
      uid: 6dfcb104-591d-435d-9fec-45e39df66a1f
    resourceVersion: "1171"
    uid: 6a1833fe-8dcd-4def-a327-cefa640840cb
  spec:
    containers:
    - image: muthukamalan/classifier-k8s
      imagePullPolicy: Always
      name: classifier
      ports:
      - containerPort: 8080
        protocol: TCP
      resources: {}
      terminationMessagePath: /dev/termination-log
      terminationMessagePolicy: File
      volumeMounts:
      - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
        name: kube-api-access-x8ppg
        readOnly: true
    dnsPolicy: ClusterFirst
    enableServiceLinks: true
    nodeName: minikube
    preemptionPolicy: PreemptLowerPriority
    priority: 0
    restartPolicy: Always
    schedulerName: default-scheduler
    securityContext: {}
    serviceAccount: default
    serviceAccountName: default
    terminationGracePeriodSeconds: 30
    tolerations:
    - effect: NoExecute
      key: node.kubernetes.io/not-ready
      operator: Exists
      tolerationSeconds: 300
    - effect: NoExecute
      key: node.kubernetes.io/unreachable
      operator: Exists
      tolerationSeconds: 300
    volumes:
    - name: kube-api-access-x8ppg
      projected:
        defaultMode: 420
        sources:
        - serviceAccountToken:
            expirationSeconds: 3607
            path: token
        - configMap:
            items:
            - key: ca.crt
              path: ca.crt
            name: kube-root-ca.crt
        - downwardAPI:
            items:
            - fieldRef:
                apiVersion: v1
                fieldPath: metadata.namespace
              path: namespace
  status:
    conditions:
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:44:01Z"
      status: "True"
      type: PodReadyToStartContainers
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:43:37Z"
      status: "True"
      type: Initialized
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:44:01Z"
      status: "True"
      type: Ready
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:44:01Z"
      status: "True"
      type: ContainersReady
    - lastProbeTime: null
      lastTransitionTime: "2024-12-25T20:43:37Z"
      status: "True"
      type: PodScheduled
    containerStatuses:
    - containerID: docker://797d3e2650d662a734207e72e848c1f7fccabd4dfc01fb7b13d6f7961636f72c
      image: muthukamalan/classifier-k8s:latest
      imageID: docker-pullable://muthukamalan/classifier-k8s@sha256:6ed53db9268c9eec1ffac6e6221c6c188ed08bcc2e4ec2568c9f990627bd147f
      lastState: {}
      name: classifier
      ready: true
      restartCount: 0
      started: true
      state:
        running:
          startedAt: "2024-12-25T20:44:01Z"
      volumeMounts:
      - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
        name: kube-api-access-x8ppg
        readOnly: true
        recursiveReadOnly: Disabled
    hostIP: 192.168.49.2
    hostIPs:
    - ip: 192.168.49.2
    phase: Running
    podIP: 10.244.0.9
    podIPs:
    - ip: 10.244.0.9
    qosClass: BestEffort
    startTime: "2024-12-25T20:43:37Z"
- apiVersion: v1
  kind: Service
  metadata:
    creationTimestamp: "2024-12-25T20:43:37Z"
    name: classifier-service
    namespace: default
    resourceVersion: "1402"
    uid: 5ffa81df-0d31-463e-b5f3-258c9b19922c
  spec:
    allocateLoadBalancerNodePorts: true
    clusterIP: 10.104.23.156
    clusterIPs:
    - 10.104.23.156
    externalTrafficPolicy: Cluster
    internalTrafficPolicy: Cluster
    ipFamilies:
    - IPv4
    ipFamilyPolicy: SingleStack
    ports:
    - nodePort: 32564
      port: 80
      protocol: TCP
      targetPort: 8080
    selector:
      app: classifier
    sessionAffinity: None
    type: LoadBalancer
  status:
    loadBalancer:
      ingress:
      - ip: 10.104.23.156
        ipMode: VIP
- apiVersion: v1
  kind: Service
  metadata:
    creationTimestamp: "2024-12-25T20:33:55Z"
    labels:
      component: apiserver
      provider: kubernetes
    name: kubernetes
    namespace: default
    resourceVersion: "198"
    uid: 895eb87f-b4e4-4681-b933-696409b2613b
  spec:
    clusterIP: 10.96.0.1
    clusterIPs:
    - 10.96.0.1
    internalTrafficPolicy: Cluster
    ipFamilies:
    - IPv4
    ipFamilyPolicy: SingleStack
    ports:
    - name: https
      port: 443
      protocol: TCP
      targetPort: 8443
    sessionAffinity: None
    type: ClusterIP
  status:
    loadBalancer: {}
- apiVersion: apps/v1
  kind: Deployment
  metadata:
    annotations:
      deployment.kubernetes.io/revision: "1"
    creationTimestamp: "2024-12-25T20:43:37Z"
    generation: 1
    labels:
      app: classifier
    name: classifier-deployment
    namespace: default
    resourceVersion: "1184"
    uid: ce7650fd-e83e-4c33-bccb-e62a47e8a7a8
  spec:
    progressDeadlineSeconds: 600
    replicas: 2
    revisionHistoryLimit: 10
    selector:
      matchLabels:
        app: classifier
    strategy:
      rollingUpdate:
        maxSurge: 25%
        maxUnavailable: 25%
      type: RollingUpdate
    template:
      metadata:
        creationTimestamp: null
        labels:
          app: classifier
      spec:
        containers:
        - image: muthukamalan/classifier-k8s
          imagePullPolicy: Always
          name: classifier
          ports:
          - containerPort: 8080
            protocol: TCP
          resources: {}
          terminationMessagePath: /dev/termination-log
          terminationMessagePolicy: File
        dnsPolicy: ClusterFirst
        restartPolicy: Always
        schedulerName: default-scheduler
        securityContext: {}
        terminationGracePeriodSeconds: 30
  status:
    availableReplicas: 2
    conditions:
    - lastTransitionTime: "2024-12-25T20:44:04Z"
      lastUpdateTime: "2024-12-25T20:44:04Z"
      message: Deployment has minimum availability.
      reason: MinimumReplicasAvailable
      status: "True"
      type: Available
    - lastTransitionTime: "2024-12-25T20:43:37Z"
      lastUpdateTime: "2024-12-25T20:44:04Z"
      message: ReplicaSet "classifier-deployment-88794f4bf" has successfully progressed.
      reason: NewReplicaSetAvailable
      status: "True"
      type: Progressing
    observedGeneration: 1
    readyReplicas: 2
    replicas: 2
    updatedReplicas: 2
- apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    annotations:
      deployment.kubernetes.io/desired-replicas: "2"
      deployment.kubernetes.io/max-replicas: "3"
      deployment.kubernetes.io/revision: "1"
    creationTimestamp: "2024-12-25T20:43:37Z"
    generation: 1
    labels:
      app: classifier
      pod-template-hash: 88794f4bf
    name: classifier-deployment-88794f4bf
    namespace: default
    ownerReferences:
    - apiVersion: apps/v1
      blockOwnerDeletion: true
      controller: true
      kind: Deployment
      name: classifier-deployment
      uid: ce7650fd-e83e-4c33-bccb-e62a47e8a7a8
    resourceVersion: "1182"
    uid: 6dfcb104-591d-435d-9fec-45e39df66a1f
  spec:
    replicas: 2
    selector:
      matchLabels:
        app: classifier
        pod-template-hash: 88794f4bf
    template:
      metadata:
        creationTimestamp: null
        labels:
          app: classifier
          pod-template-hash: 88794f4bf
      spec:
        containers:
        - image: muthukamalan/classifier-k8s
          imagePullPolicy: Always
          name: classifier
          ports:
          - containerPort: 8080
            protocol: TCP
          resources: {}
          terminationMessagePath: /dev/termination-log
          terminationMessagePolicy: File
        dnsPolicy: ClusterFirst
        restartPolicy: Always
        schedulerName: default-scheduler
        securityContext: {}
        terminationGracePeriodSeconds: 30
  status:
    availableReplicas: 2
    fullyLabeledReplicas: 2
    observedGeneration: 1
    readyReplicas: 2
    replicas: 2
kind: List
metadata:
  resourceVersion: ""
ubuntu@ip-172-31-9-129:~/mlops_kubernetes$
```
