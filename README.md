# test-chart
test chart for nginx

# create chart
`helm create nginx`

# start minikube
`minikube start`

# init helm on minikube
`../helm-init.sh`

or

`kubectl -n kube-system create sa tiller`
`kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller`
`helm init --service-account tiller`


# install chart
`helm install ./nginx --name nginx --namespace default`

# if testing locally, modify /etc/hosts
`sudo vim /etc/hosts`

add entry for `chart-example.local` to point to minikube address `192.168.99.100`.

# test ingress.  subsitute 31055 with the node port of nginx service.
`kubectl get svc nginx`
`curl -v chart-example.local:31055`
