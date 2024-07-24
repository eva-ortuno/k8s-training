# Instructions : 

- Create the 2 namespaces
`kubectl create namespace namespace-a`
`kubectl create namespace namespace-b`

- Enable istio
`kubectl label namespace namespace-a istio-injection=enabled`
`kubectl label namespace namespace-b istio-injection=enabled`

- Deploy service a :
`kubectl apply -f busybox.yaml`

- Deploy service b 
`kubectl apply -f service-b-deployment.yaml`

- Deploy service entry 
`kubectl apply -f service-entry.yaml`

- Deploy the auth policy 
`kubectl apply -f authorization-policy.yaml`

then start the pod : `kubectl exec -it -n namespace-a busybox -- sh` 
and send a curl request to service B : `curl http://service-b.namespace-b.svc.cluster.local:80`
