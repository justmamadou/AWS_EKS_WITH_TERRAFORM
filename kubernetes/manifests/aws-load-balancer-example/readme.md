# Testing aws load balancer controller

### Check if the aws-load-balancer-controller pod was deployed
```bash
kubectl get  pod -n kube-system
```
![alt text](image.png)

### Deploy the app and check if the load balancer aws creates

![alt text](image-1.png)

### check if the load balancer will redirect the traffic
![alt text](image-2.png)