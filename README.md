# t02 IOC Instances and Services Deployment Repository for Argo CD

This repository holds the definition of Argocd deployed ec services. Each sub folder of the 'services' directory of an ec 'services repository' is mapped to an Argocd App which is managed by a root App.

## Deployment
To deploy the Argocd root App:
```
source environment.sh
argocd app create --file apps.yaml
```

## Adding webhooks
By default argocd will poll Git repositories for changes to manifests every 3 minutes. In order to have your changes applied to your app more promtly one could:
- Trigger a refresh using the cli or web UI
- Configure a webhook so that their git provider can trigger refreshes immediately

For more details: https://argo-cd.readthedocs.io/en/latest/operator-manual/webhook/

### Instructions for internal Gitlab

1. Navigate to your repo hosted in Gitlab
1. Select Project -> Settings -> Webhooks
1. Select "Add new webhook"
1. Enter the url: `<your_argocd_server>/api/webhook` (for example: https://argocd.diamond.ac.uk/api/webhook)
1. Under "Trigger" tick "Push events"
1. Finally select "Save changes"
