# cicd-jenkinsx-argocd

Pre requistes for running this sample:

Kubernetes should be installed
Jenkinx should be installed
Helm Charts should be installed
Argocd should be installed
Argo CLi should be installed
Running the sample:

1) From Jenkinsx pipeline, create a new pipeline shoosing this repo

2) Pipeline gets created

In Jenkins file, where we execute deploy step, make sure we change the values of below as appropriate 

sh 'PATH=$PATH:$PWD/ && argocd login $ARGOCD Server --username admin --password $argocdpassword --insecure && argocd app 
create guestbook --name=guestbook --repo https://github.com/RajeshAjjarapu/guestbook_jenkins_argocd.git --path=env 
--dest-server https://kubernetes.default.svc --dest-namespace jx'

3) Sync the pipeline and the sameple runs both CI and we would see instances deployed on Argo CD as well
