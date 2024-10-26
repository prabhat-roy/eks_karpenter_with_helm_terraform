Run terraform apply -auto-approve to create EKS cluster

Update kubeconfig to connect kubernetes cluster

aws eks update-kubeconfig --region ap-south-2 --name EKS-Cluster

Check the karpenter namespace

helm list -A
kubectl get pods -n karpenter

Create Karpenter Provisioner

kubectl apply -f provisioner.yaml

Create a deployment

kubectl apply -f deployment.yaml

Scale up the deployment

kubectl scale deployment nginx-deployment --replicas 20 

Check the nodes which were added

kubectl get nodes

Scale down the deployment

kubectl scale deployment nginx-deployment --replicas 1

Check the nodes which were removed

kubectl get nodes

Delete the deployment

kubectl delete -f deployment.yaml

Destroy the entire infrastructure

terraform destroy -auto-approve
