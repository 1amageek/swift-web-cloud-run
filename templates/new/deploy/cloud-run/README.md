# Cloud Run

This template provides a container scaffold for SwiftWeb's Vapor host adapter.

```bash
docker build -f deploy/cloud-run/Dockerfile -t {{app.kebabName}} .
docker run --rm -p 8080:8080 -e PORT=8080 {{app.kebabName}}
```

