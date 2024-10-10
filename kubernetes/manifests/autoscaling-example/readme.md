# Testing Cluster Autoscaling

### First get the number of nodes
```bash
kubectl get  nodes
```
![alt text](image.png)


### Deploy the application
```bash
kubectl apply -f autoscaling-example/
```
![alt text](image-1.png)

### Check the number of nodes now
```bash
kubectl get  nodes -w 
```
![alt text](image-2.png)