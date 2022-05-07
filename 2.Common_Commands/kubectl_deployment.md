- Create nginx deployment with the latest nginx:
```
kubectl create deployment nginx-deployment --image=nginx
```

- Also you can create deployment to specific namespace ( example is namespace: `kienlt` )
```
kubectl create deployment nginx-deployment --image=nginx -n kienlt
```

