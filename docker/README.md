# fever-prueba
 Prueba técnica 2024 Oscar Reyes


#In this readme, you will find all the steps that I did in order to get the desire setup.
#For this setup, 2 python scripts were provided (called server.py and client.py) this 
#applications must be created with an image and therefore distributed in a kubernetes cluster.



Nginx installed, associated with an ingress-nginx resource.

Tested service through the client pod with curls towards the nginx ingress controller service
Changing the classname, it gives an 503 error instead of 404 in the begining. I supposed this change is due to have a backend service behind the aforementioned resource.

Analysis and investigation to check whether this error occurs and how to implement an stable connectivity path (check the logs from the proper backend in order to know if it reaches correctly. Additionally, checking the nginx logs to have a better understanding of the behavior) .


kubectl label nodes fever-cluster-control-plane ingress-ready=true
kubectl create -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml

kubectl get pods -n ingress-nginx
NAME                                        READY   STATUS      RESTARTS   AGE
ingress-nginx-admission-create-9wvsf        0/1     Completed   0          68s
ingress-nginx-admission-patch-m5svm         0/1     Completed   1          68s
ingress-nginx-controller-6f5b7cc8d4-x5lx8   1/1     Running     0          68s

https://kind.sigs.k8s.io/docs/user/ingress/


passthrough ssl 
https://arunsworld.medium.com/ssl-passthrough-via-kubernetes-ingress-b3eaf3c7c9da

Later on, https://kubernetes.github.io/ingress-nginx/user-guide/nginx-configuration/annotations/#ssl-passthrough 	

Export files was made with kubectl cluster-info dump --all-namespaces --output-directory dump-cluster -o yaml
