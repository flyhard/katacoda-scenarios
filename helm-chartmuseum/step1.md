## Launch kubernetes

`launch.sh`{{execute}}

## Install Helm into your cluster

Deploy helm to you cluster

`curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > get_helm.sh ; chmod +x get_helm.sh ; ./get_helm.sh`{{execute}}

## Initialize Helm

`helm init`{{execute}}

then wait for tiller to be ready:

`kubectl get pod -n kube-system -l app=helm -l name=tiller`{{execute}}

## Install chartmuseum

`helm upgrade --install chartmuseum stable/chartmuseum --set env.open.DISABLE_API=false`{{execute}}

## Add the helm plugin for chartmuseum

`helm plugin install https://github.com/chartmuseum/helm-push`{{execute}}

## Add a portforward so you can use chartmuseum 

`export POD_NAME=$(kubectl get pods --namespace default -l "app=chartmuseum" -l "release=chartmuseum" -o jsonpath="{.items[0].metadata.name}")
echo http://127.0.0.1:8080/
kubectl port-forward $POD_NAME 8080:8080 --namespace default &`{{execute}}

Now chartmuseum should be ready to use at

https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

## Now add chartmuseum as a helm repo

`helm repo add chartmuseum http://localhost:8080/`{{execute}}

and verify it is there:

`helm repo list`{{execute}}