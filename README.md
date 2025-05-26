````markdown
# n8n k3s Kubernetes Stack

A simple and scalable n8n stack for a k3s Kubernetes cluster using the official n8n Docker image.

![20250526_1157_Automated Workflow Platform_simple_compose_01jw6093q5e1wst9m447wch0nz](https://github.com/user-attachments/assets/4d953cf0-5652-49a8-bebc-fbfd573f51fc)

## Prerequisites

- A running k3s Kubernetes cluster
- kubectl CLI configured to access your cluster
- Helm (optional, if you choose to use Helm charts)

## Installation

```bash
# Create the namespace
kubectl create namespace n8n

# Deploy the n8n stack (apply manifests recursively)
kubectl apply -f ./ -n n8n --recursive
````

## Uninstallation

```bash
# If installed via Helm
helm uninstall n8n --namespace n8n

# Delete the namespace
kubectl delete namespace n8n
```

## Accessing n8n

```bash
# Get the ingress IP address
kubectl get ingress n8n-ingress -n n8n -o jsonpath='{.status.loadBalancer.ingress[0].ip}'

# Open in browser (replace <ingress-ip> with the actual IP)
open http://<ingress-ip>
```

## Cloudflare Integration

This stack exposes the n8n service via Cloudflare by default.
You can easily switch to other ingress controllers like NGINX or Traefik based on your preference.

---

## Troubleshooting & FAQ

* Make sure your ingress controller is properly configured.
* Ensure your DNS settings in Cloudflare point to the correct ingress IP.
* If using Helm, confirm the chart version compatibility.


