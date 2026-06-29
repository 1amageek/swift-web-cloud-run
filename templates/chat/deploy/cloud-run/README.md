# Cloud Run Chat Template

This template provides a container scaffold for a SwiftWeb chat app running on
SwiftWeb's Vapor host adapter.

```bash
docker build -f deploy/cloud-run/Dockerfile -t {{app.kebabName}}-chat .
docker run --rm -p 8080:8080 -e PORT=8080 {{app.kebabName}}-chat
```

