# Task 1: Create Your First Pod (Nginx)
 
 vim nginx.yml
 
 kind: Pod
 apiVersion: v1
  
 metadata:
    name: nginx
   
 spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80


opstree@opstree-Latitude-3420:~$ kubectl get pods 

NAME    READY   STATUS    RESTARTS       AGE

nginx   1/1     Running   1 (126m ago)   19h

opstree@opstree-Latitude-3420:~$ cd devops/kubernetes-practise/

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ vim nginx-pod.yml 

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl port-forward nginx 8081:80 

Forwarding from 127.0.0.1:8081 -> 80

Forwarding from [::1]:8081 -> 80

Handling connection for 8081

Handling connection for 8081

# Task 2: Create a Custom Pod (BusyBox)

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ vim busybox-pod.yml

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl apply -f busybox-pod.yml 

pod/busybox created

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl get pods 

NAME      READY   STATUS    RESTARTS       AGE

busybox   1/1     Running   0              19s

# Task 3: Imperative vs Declarative

## Imparative means

Imparative means creating the pods without YML file 

## Declarative means 

Declarative means creating pods through yml file. 

### tried to create a redis pod with imparative command 

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl run redis-pod --image=redis:latest
pod/redis-pod created
opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl get pod redis-pod -o yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: "2026-03-26T10:17:43Z"
  generation: 1
  labels:
    run: redis-pod
  name: redis-pod
  namespace: default
  resourceVersion: "79791"
  uid: d0e05769-01bc-4059-b817-25e371b1a106
spec:
  containers:
  - image: redis:latest
    imagePullPolicy: Always
    name: redis-pod
    resources: {}
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: kube-api-access-nng6t
      readOnly: true
  dnsPolicy: ClusterFirst
  enableServiceLinks: true
  nodeName: my-cluster-worker3
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
  - name: kube-api-access-nng6t
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
    lastTransitionTime: "2026-03-26T10:18:07Z"
    observedGeneration: 1
    status: "True"
    type: PodReadyToStartContainers
  - lastProbeTime: null
    lastTransitionTime: "2026-03-26T10:17:43Z"
    observedGeneration: 1
    status: "True"
    type: Initialized
  - lastProbeTime: null
    lastTransitionTime: "2026-03-26T10:18:07Z"
    observedGeneration: 1
    status: "True"
    type: Ready
  - lastProbeTime: null
    lastTransitionTime: "2026-03-26T10:18:07Z"
    observedGeneration: 1
    status: "True"
    type: ContainersReady
  - lastProbeTime: null
    lastTransitionTime: "2026-03-26T10:17:43Z"
    observedGeneration: 1
    status: "True"
    type: PodScheduled
  containerStatuses:
  - containerID: containerd://a450c1d9d746bab354250458c76a7ab60c0efb491e6d62bed8517fbbb7636364
    image: docker.io/library/redis:latest
    imageID: docker.io/library/redis@sha256:009cc37796fbdbe1b631b4cc0582bed167e5e403ed8bcd06f77eb6cb5aeb6f93
    lastState: {}
    name: redis-pod
    ready: true
    resources: {}
    restartCount: 0
    started: true
    state:
      running:
        startedAt: "2026-03-26T10:18:06Z"
    user:
      linux:
        gid: 0
        supplementalGroups:
        - 0
        uid: 0
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: kube-api-access-nng6t
      readOnly: true
      recursiveReadOnly: Disabled
  hostIP: 172.18.0.5
  hostIPs:
  - ip: 172.18.0.5
  observedGeneration: 1
  phase: Running
  podIP: 10.244.2.2
  podIPs:
  - ip: 10.244.2.2
  qosClass: BestEffort
  startTime: "2026-03-26T10:17:43Z"

### Task 6: Clean Up

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl delete pod nginx-pod

kubectl delete pod busybox-pod

kubectl delete pod redis-pod

Error from server (NotFound): pods "nginx-pod" not found

Error from server (NotFound): pods "busybox-pod" not found

pod "redis-pod" deleted from default namespace

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl delete pod redis-pod

Error from server (NotFound): pods "redis-pod" not found

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl delete -f busybox-pod.yml 

pod "busybox" deleted from default namespace

opstree@opstree-Latitude-3420:~/devops/kubernetes-practise$ kubectl delete pod nginx

pod "nginx" deleted from default namespace
