# CRUD App on Kubernetes

This project sets up a simple CRUD application with a PostgreSQL database using Kubernetes manifests.

---

## Instructions

### Start the Application

```sh
kubectl apply -f namespace.yaml --wait # wait for the crud-app namespace to get created
kubectl config set-context --current --namespace=crud-app # set namespace in current context
kubectl apply -f . # create other resources

# once all resources are created successfully
kubectl port-forward service/backend-service 8000:8000 # port forwarding to access service
```

### Test

```sh
curl -X GET http://localhost:8000/users
curl -X POST http://localhost:8000/users -d '{"name":"John Doe", "email":"jdoe@example.com"}' -H "Content-Type: application/json"
curl -X GET http://localhost:8000/users
```

### Stop application

```sh
# delete all the resources
kubectl delete -f .
```
 