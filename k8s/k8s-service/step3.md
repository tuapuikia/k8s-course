Deploy nginx with k8s LoadBalancer service.

`kubectl apply -f ./nginx-lb.yaml`{{execute HOST1}}


View the nginx.yaml content

`cat nginx-lb.yaml`{{execute HOST1}}

Verify pod and service are created.

`kubectl get pod && kubectl get service`{{execute HOST1}}

Test the nginx service using clusterIP service.

`kubectl run -ti --rm busybox --image=busybox --restart=Always`{{execute HOST1}}

Verify nginx service is accessible.

`wget nginx`{{execute HOST1}}
`cat index.html`{{execute HOST1}}
