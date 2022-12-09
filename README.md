# Knative Serving Kustomization

For use with [FluxCD](https://fluxcd.io) to deploy [Knative Serving](https://knative.dev)

## Add the GitRepository

```bash
flux create source git knative-serving \
  --url=https://github.com/dashaun-cloud/knative-serving-kustomization \
  --branch=main \
  --interval=30s \
  --export > ./clusters/cluster00/knative-serving-kustomization-source.yaml
```

## Add the Kustomization

```bash
flux create kustomization knative-serving \
  --target-namespace=default \
  --source=knative-serving \
  --path="./kustomize" \
  --prune=true \
  --interval=5m \
  --export > ./clusters/cluster00/knative-serving-kustomization.yaml
```