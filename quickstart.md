# Argo CD Flask Demo

A minimal Flask app for learning GitOps with Argo CD and Minikube. The app
displays **Hello from Argo CD!** and explains that it is deployed through
GitOps.

## Prerequisites

- Docker
- Minikube
- `kubectl`

## Build and load the image

From the project root, build the image:

```sh
docker build -t argocd-flask-demo:latest .
```

Load it into Minikube:

```sh
minikube image load argocd-flask-demo:latest
```

## Deploy with kubectl

Apply the manifests:

```sh
kubectl apply -f k8s/
```

Check that the pod is ready:

```sh
kubectl get deployment,pods,services
```

## Access the app locally

The Service is internal to the cluster (`ClusterIP`). Forward its port:

```sh
kubectl port-forward service/argocd-flask-demo 5000:5000
```

Open <http://localhost:5000>.

The manifests in `k8s/` can also be selected as the repository path when
configuring Argo CD to sync this repository.
