# Kubernetes live interview

## 1. Start Nginx
Create a Kubernetes deployment to run **Nginx** you can use the `nginx:latest` image from dockerhub.

You must deploy it in the namespace `interview-test`

## 2. Connect a kubernetes service
Use a Kubernetes service of type `ClusterIp` to connect to your Nginx deployment.

Verify the connectivity using curl from your vscode instance.

## 3. Deploy a postgres database using Helm

Use Helm to deploy a postgres database. The [following chart](https://artifacthub.io/packages/helm/bitnami/postgresql) **must** be used.

The following requirement must be met:
- Create a dedicated file with **ONLY** the overwritten values `interview-vals.yaml`
- Disable **persistance** of the data
- Set **Limit of CPU** to `750m` and **Limit of RAM** to `1Gi`