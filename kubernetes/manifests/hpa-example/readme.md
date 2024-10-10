# Test the Horizontal Pod Autoscaling

### First deploy the application
```bash
kubectl apply -f hpa-example/
```
![alt text](image-2.png)
### Port-forwarding
```bash
kubectl port-forward svc/myapp 8080 -n hpa-example
```
![alt text](image.png)

### Generate Traffic
```bash
curl "localhost:8080/api/cpu?index=44"
```
![alt text](image-1.png)