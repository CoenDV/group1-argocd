# Group1 ArgoCD Configuration

This repository contains ArgoCD Application manifests for deploying Group1 microservices to Kubernetes.

## Structure

```
group1-argocd/
├── production/          # Production environment (main branch)
│   ├── kustomize.yaml
│   ├── chatservice.yaml
│   ├── communityservice.yaml
│   ├── notificationservice.yaml
│   ├── recommendationservice.yaml
│   ├── userservice.yaml
│   └── videoservice.yaml
└── test/               # Test environment (dev branch)
    ├── kustomize.yaml
    ├── chatservice.yaml
    ├── communityservice.yaml
    ├── notificationservice.yaml
    ├── recommendationservice.yaml
    ├── userservice.yaml
    └── videoservice.yaml
```

## Environments

### Production (`projectgroup1-prod`)
- **Branch:** `main`
- **Namespace:** `projectgroup1-prod`
- Deploys stable releases from main branch

### Test (`projectgroup1-test`)
- **Branch:** `dev`
- **Namespace:** `projectgroup1-test`
- Deploys development versions from dev branch

## Services

| Service | Repository |
|---------|-----------|
| Kustomize | [simpleSlideshow-deploy](https://github.com/CoenDV/simpleSlideshow-deploy.git) |
| Chat Service | [Group1-ChatService](https://github.com/InHolland-Cloud-Minor-2526/Group1-ChatService) |
| Community Service | [Group1-CommunityService](https://github.com/InHolland-Cloud-Minor-2526/Group1-CommunityService) |
| Notification Service | [Group1-NotificationService](https://github.com/InHolland-Cloud-Minor-2526/Group1-NotificationService) |
| Recommendation Service | [Group1-RecommendationService](https://github.com/InHolland-Cloud-Minor-2526/Group1-RecommendationService) |
| User Service | [Group1-UserService](https://github.com/InHolland-Cloud-Minor-2526/Group1-UserService) |
| Video Service | [Group1-VideoService](https://github.com/InHolland-Cloud-Minor-2526/Group1-VideoService) |

## Sync Policy

All applications are configured with:
- **Automated sync:** Changes are automatically deployed
- **Prune:** Removed resources are automatically deleted
- **Self-heal:** Cluster state is automatically corrected if manually modified

## Deployment

Apply all production applications:
```bash
kubectl apply -f production/
```

Apply all test applications:
```bash
kubectl apply -f test/
```

Apply a specific service:
```bash
kubectl apply -f production/chatservice.yaml
```
