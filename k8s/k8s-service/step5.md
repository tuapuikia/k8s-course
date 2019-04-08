Deploy nginx ingress via helm.

`wget https://raw.githubusercontent.com/helm/helm/master/scripts/get -O helm.sh && bash ./helm.sh`{{execute HOST1}}

Initialize helm tiller.

`helm init`

`kubectl create clusterrolebinding add-on-cluster-admin --clusterrole=cluster-admin --serviceaccount=kube-system:default`{{execute HOST1}}

Verify helm installation

`helm list`{{execute HOST1}}

Install nginx ingress chart

`helm install --name my-ingress stable/nginx-ingress`{{execute HOST1}}

Please note, katacoda do not provide LoadBalancer service. But we can still access the internal service to verify the setup.

`kubectl apply -f nginx-ingress.yaml`{{execute HOST1}}

Review the nginx-ingress.yaml

`cat nginx-ingress.yaml`{{execute HOST1}}

Verify the nginx ingress working correctly. (nginx ingress controller image is quite big, please be patient)

`kubectl get pod`{{execute HOST1}}

Validate out nginx services is serving via ingress controller

`kubectl run -ti --rm busybox --image=busybox --restart=Always`{{execute HOST1}}

Retrieve the nginx index.html

`wget --header 'Host: example.com' my-ingress-nginx-ingress-controller`

`cat index.html`

Exit the busybox pod

`exit`{{execute HOST1}}
