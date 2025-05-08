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
