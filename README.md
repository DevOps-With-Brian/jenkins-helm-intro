# jenkins-helm-intro
A intro repo showing all about [Jenkins as Code](https://www.jenkins.io/projects/jcasc/) using helm and kubernetes.

# Setup
Ensure you have [Helm](https://helm.sh/docs/intro/install/) installed prior to running anything below.

1. Add the repo to helm:

`helm repo add jenkins https://charts.jenkins.io`
`helm repo update`

2. Install the chart via the following command:

`helm install jenkins/jenkins --generate-name -f jenkins-helm-values.yaml`

Now you should get output similar to above which tells you how to get the admin pw and the commands to get to the url:

```
NAME: jenkins-1665132306
LAST DEPLOYED: Fri Oct  7 04:45:07 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
1. Get your 'admin' user password by running:
  kubectl exec --namespace default -it svc/jenkins-1665132306 -c jenkins -- /bin/cat /run/secrets/additional/chart-admin-password && echo
2. Get the Jenkins URL to visit by running these commands in the same shell:
  export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services jenkins-1665132306)
  export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
  echo http://$NODE_IP:$NODE_PORT/login

3. Login with the password from step 1 and the username: admin
4. Configure security realm and authorization strategy
5. Use Jenkins Configuration as Code by specifying configScripts in your values.yaml file, see documentation: http:///configuration-as-code and examples: https://github.com/jenkinsci/configuration-as-code-plugin/tree/master/demos

For more information on running Jenkins on Kubernetes, visit:
https://cloud.google.com/solutions/jenkins-on-container-engine

For more information about Jenkins Configuration as Code, visit:
https://jenkins.io/projects/jcasc/


NOTE: Consider using a custom image with pre-installed plugins
```