# k8s-tuts
Kubernetes from zero to hero.
K8s commands
Kubernetes Commands

1. Create cluster 
       kind create cluster --name k8s-tuts
  2.  Get cluster information using context
         kubectl cluster-info --context kind-k8s-tuts
  3.  Create namespace
          kubectl create namespace demo
  4.  Use context 
         kubectl config use-context kind-k8s-tuts
   5. Get nodes inside namespace
        kubectl get nodes -n demo
  6.  List pod inside namespace
        kubectl  get pod -n demo
  7.  Create pod using .yml or .yaml file
       kubectl apply -f pod.yml
  8. Delete pod in namespace
      kubectl delete pod nginx -n demo
  9.  Port forwarding 
       kubectl port-forward demopod 2224:80
  10. List all nodes necessary to build a fully functional cluster 
       kubectl top nodes (This should result Metrics API not available)
       Hence run the below command to install necessary metrics
  11. kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

 12. Verify metric api service with command
       kubectl get apiservice | grep metrics
13.  Command to patch it with self signed certs for local setup
       kubectl patch deployment metrics-server -n kube-system \
  --type=json \
  -p='[{"op":"add","path":"/spec/template/spec/containers/0/args/-","value":"--kubelet-insecure-tls"}]'
14. List top nodes which are notes required to fetch metrics about others nodes in a cluster
      kubectl top nodes
15. List all the top nodes in all namespaces : kubectl top nodes -A
16. Describe namespace: kubectl describe ns demo
17. List all quotas in demo namespace: kubectl get quota 
18. Describe quota: kubectl describe resourcequota tiny-rq -n demo
19. Watch pods memory and cpu size in namespace: watch -n 0.1 kubectl describe ns demo
20. Create config map: kubectl create configmaps dem-heroes —from-file=heroes.txt
21. Create secret from command line. Kubectl create secret generic mysql-secret —type=kubernetes.io/basic-auth --from-literal=password=alta3
22. Annotating pods with labels and listing them: a) kubectl label pod demo-pod awesome=sauce -n demo. b) kubectl get pods —show-labels    


         
 
