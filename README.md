````md
# n8n k3s (Kubernetes) Stack

A simple and scalable n8n stack for k3s (Kubernetes) using the official n8n Docker image.

## Prerequisites

- k3s cluster up and running
- kubectl CLI configured
- Helm (optional, if using Helm charts)

## Installation

```bash
# Create namespace
kubectl create namespace n8n

# Deploy n8n stack (apply manifests recursively)
kubectl apply -f ./ -n n8n --recursive
````

## Uninstallation

```bash
helm uninstall n8n --namespace n8n
kubectl delete namespace n8n
```

## Accessing n8n

```bash
# Get ingress IP address
kubectl get ingress n8n-ingress -n n8n -o jsonpath='{.status.loadBalancer.ingress[0].ip}'

# Open in browser (replace <ingress-ip> with actual IP)
open http://<ingress-ip>
```

## Cloudflare Integration

This stack exposes n8n service via Cloudflare by default.
You can easily switch to other ingress controllers like NGINX or Traefik based on your preference.

---

### Suggested improvements

* Use consistent terminology: e.g., replace "k3s (Kubernetes)" with "k3s Kubernetes cluster".
* Add Helm usage instructions if Helm is required.
* Fix minor typos:

  * "ingres" → "ingress"
  * Capitalize proper nouns (e.g., "Cloudflare", "NGINX", "Traefik").
* Use `kubectl apply -f ./ -n n8n --recursive` instead of `-R` for clarity.
* Clarify that uninstallation assumes Helm was used.
* Optionally add a troubleshooting or FAQ section.
* Consider adding badge/status indicators (build, license).


