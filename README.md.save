# Simple FastAPI Application

A lightweight FastAPI app with a Jenkins CI/CD pipeline, Docker image, and Kubernetes deployment.

## Endpoints

| Method | Path              | Description                     |
|--------|-------------------|---------------------------------|
| GET    | `/`               | Welcome / health check          |
| GET    | `/items/{item_id}`| Path + optional query parameter |
| POST   | `/items/`         | Create item (Pydantic body)     |

Interactive docs: `http://localhost:8000/docs`

## Run locally

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload
```

## Run tests

```bash
pip install -r requirements-dev.txt
pytest -v
```

## Run with Docker

```bash
docker build -t my-fastapi-app .
docker run -p 8000:8000 my-fastapi-app
```

## Deploy to Kubernetes manually

```bash
sed -i 's|IMAGE_PLACEHOLDER|your-dockerhub-username/my-fastapi-app:latest|' k8s/deployment.yaml
kubectl apply -f k8s/
kubectl get pods,svc
```

Access via `http://<node-ip>:30080`.

## CI/CD pipeline (Jenkins)

Stages: Checkout → Install & Test → Build Image → Push Image → Deploy to Kubernetes.

Required Jenkins credentials:

| ID               | Type                  | Purpose                  |
|------------------|-----------------------|--------------------------|
| `dockerhub-creds`| Username with password| Push images to Docker Hub|
| `kubeconfig`     | Secret file           | kubectl access to cluster|

The Jenkins agent needs Python 3, Docker, and kubectl installed.
