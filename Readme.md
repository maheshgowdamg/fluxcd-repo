Flux Bootstrap
flux bootstrap github \
--owner=maheshgowdamg \
--repository=fluxcd-repo \
--path=flux-cluster/dev-cluster \
--personal=true \
--private=false


create the gitrepository for watch my helm chart repo
------------------------------------------------------------
flux create source git gitrepository \
--url https://github.com/maheshgowdamg/springboot-app.git \
--branch main \
--timeout 10s \
--export > C:/Users/Mahesh.G/Desktop/fluxcd-repo/flux-cluster/dev-cluster/gitrepository.yaml


flux helmrelease 
-----------------
flux create helmrelease helmrelease \
--chart mychart \
--interval 10s \
--target-namespace demo \
--source GitRepository/gitrepository \
--export > helmrelease.yaml


Commands:
*flux get all
*flux get source git <namespace>
*flux get sources git all
*flux get helmrelease
*kubectl get helmcharts.source.toolkit.fluxcd.io
*kubectl get pods -n 
*kubectl get all <namespace>
*kubectl exec -it  source-controller-6ff87cb475-ftdp5 -n flux-system -- sh(to check)



weavegitops for flux UI
------------------------
Go to weavegitops.org
-docs-->
Step 1 - Install Weave GitOps Open Source
------------------------------------------
curl command:
curl --silent --location "https://github.com/weaveworks/weave-gitops/releases/download/v0.38.0/gitops-$(uname)-$(uname -m).tar.gz" | tar xz -C /tmp
sudo mv /tmp/gitops /usr/local/bin
gitops version


or 

curl --location "https://github.com/weaveworks/weave-gitops/releases/download/v0.17.0/gitops-linux-x86_64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/gitops /usr/local/bin

step2- Create dashboard for fluxui
----------------------------------
gitops create dashboard ww-gitops \
  --password=$PASSWORD \

step3-Get all resource in flux-system namespace
-----------------------------------------------
kubectl get all -n flux-system

step4-Edit service part expose outside cluster
----------------------------------------------
kubectl edit svc -n flux-system <service-name>
