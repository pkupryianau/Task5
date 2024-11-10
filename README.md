# Task 5: Simple Application Deployment with Helm

## Objective

In this Task5 was created kubernetes infrastructure based on k3s cluster and deployed application WordPress based on  HELM. Deploy application was created on  ArgoCD.

## Steps

1. **Create k3s cluster**
   - Create cluster based on  k3s.
        - curl -sfL https://get.k3s.io | sh -
        - sudo k3s kubectl get node

2. **Install Helm**
   - Install Helm
        - curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3

3. **Install ArgoCD**
   - Install ArgoCD
        - create additional namespace for deploy and install ArgoCD (kubectl create namespace argocd)
        - install ArgoCD (wget https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml -O install.yaml)
        - reconfig ArgoCD ( create secret files, configure netowk svc-service to using LoadBalancer and  providing access gui    ArgoCD   from  internet)
          - screen [argocd](images/argo_cd_install.png)
          - screen [argocd_gui](images/argo_cd_gui.png)
        - create configuration Helm files for deploy WordPress (Chart.yaml, directory mysql,wordpress)

4. **Configure ArgoCd to deploy Helm charts**
   - Configure ArgoCD for use Github repo
        - screen [github](images/argocd_helm_repo.png)
   - Configure start application  on  ArgoCD to deploy.
        - screen [appl](images/argocd_helm_mysql.png)
   - Configure ArgoCD for deploy applicationmysql, wordpress .
        - screen [config](images/create_wp_mysql.png)
5. **Deploy an application  WordPress on  ArgoCD based Helm carts**
   - Deploy a simple task
       - screen [deploy](images/create_wp_mysql.png)
       - screen [wp_site](images/wp_site.png)
