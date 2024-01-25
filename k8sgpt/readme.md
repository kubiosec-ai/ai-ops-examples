```
kubectl apply -f - << EOF
apiVersion: core.k8sgpt.ai/v1alpha1
kind: K8sGPT
metadata:
  name: k8sgpt-sample
  namespace: k8sgpt-operator-system
spec:
  ai:
    enabled: true
    model: gpt-3.5-turbo
    backend: openai
    secret:
      name: k8sgpt-sample-secret
      key: openai-api-key
    # anonymized: false
    # language: english
  noCache: false
  version: v0.3.25
  # filters:
  #   - Ingress
  # sink:
  #   type: slack
  #   webhook: <webhook-url>
  # extraOptions:
  #   backstage:
  #     enabled: true
EOF
```

```
kubectl create secret generic k8sgpt-sample-secret --from-literal=openai-api-key=xxxxxxxxxx -n default
```
