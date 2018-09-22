This guide follows the one built by the ambassador team here:
https://www.getambassador.io/user-guide/getting-started

Modified to use only 1 replica is this is for DEV only.

Step 1 is required for GKE which uses RBAC and needs additional permission role binding. 
Step 2 installs the RBAC version of ambasador as a NodePort service
Step 3 of the steps setup the ambassodor service
Step 4 create a sample application which redirects to httpbin
Steps 5 & 6 are verification steps

Step 7 - host a small spring-boot application

1. kubectl create clusterrolebinding my-cluster-admin-binding --clusterrole=cluster-admin --user=$(gcloud info --format="value(config.account)")
2. kubectl apply -f https://getambassador.io/yaml/ambassador/ambassador-rbac.yaml
3. kubectl apply -f ambassador-service.yaml
4. kubectl apply -f httpbin.yaml
5. kubectl get svc -o wide ambassador
6. curl 35.36.37.38/httpbin/