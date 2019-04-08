Deploy nginx with k8s NodePort service.

`kubectl apply -f ./nginx-np.yaml`{{execute HOST1}}

View the nginx.yaml content

`cat nginx-np.yaml`{{execute HOST1}}

Verify pod and service are created.

`kubectl get pod && kubectl get service`{{execute HOST1}}

The nginx now are accessible from external via worker node port.

Before we can access the service, we need to locate our worker node IP

`kubectl get node -o wide`{{execute HOST1}}

Find our nodeport port that listen on worker node.

`kubectl get service nginx-np -o yaml | grep nodePort`{{execute HOST1}}

Access the nginx using worker node IP and nginx node port service port.

Export the node IP to environment variable.

`export NODEIP=$(kubectl  get node -o wide | grep node01 | awk '{print $6}')`{{execute HOST1}}

Export node port to environment variable.

`export NODEPORT=$(kubectl get service nginx-lb -o yaml | grep nodePort | awk '{print $3}')`{{execute HOST1}}

Retrieve the index.html

`wget $NODEIP:$NODEPORT`{{execute HOST1}}

Verify the nginx sample page content.

`cat index.html`{{execute HOST1}}
