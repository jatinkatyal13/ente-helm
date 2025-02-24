# Ente Helm
![Version: 0.1.2](https://img.shields.io/badge/Version-0.1.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.16.0](https://img.shields.io/badge/AppVersion-1.16.0-informational?style=flat-square)
## Introduction

This repository contains Helm charts for deploying various applications and services on my personal Raspberry Pi cluster. The cluster is part of my home lab setup, allowing me to experiment with Kubernetes and Helm in a controlled environment. These charts are tailored to run efficiently on ARM architecture, making them ideal for Raspberry Pi devices.

## Deploy the Helm Chart

1. Add the Helm repo:
    ```sh
    helm repo add ente-helm https://jatinkatyal13.github.io/ente-helm/
    helm repo update
    ```

2. Install the chart with the release name `my-release`:
    ```sh
    helm install my-release ente-helm/ente-helm
    ```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"ghcr.io/ente-io/server"` |  |
| image.tag | string | `"latest"` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.enabled | bool | `true` |  |
| persistence.size | string | `"10Gi"` |  |
| persistence.storageClass | string | `"longhorn"` |  |
| replicaCount | int | `1` |  |
| service.port | int | `8080` |  |
| service.type | string | `"ClusterIP"` |  |


## How to Run Helmdocs and Generate Docs

To generate documentation for your Helm charts using Helmdocs, follow these steps:

1. Install Helmdocs:
    ```sh
    go get github.com/norwoodj/helm-docs/cmd/helm-docs
    ```

2. Navigate to the directory containing your Helm charts:
    ```sh
    cd /path/to/your/helm/charts
    ```

3. Run Helmdocs to generate the documentation:
    ```sh
    helm-docs
    ```

## How to Run Helm Template and Test the Output

To render your Helm templates and test the output, use the following commands:

1. Navigate to the directory containing your Helm charts:
    ```sh
    cd /path/to/your/helm/charts
    ```

2. Run the `helm template` command to render the templates:
    ```sh
    helm template my-release .
    ```

3. To test the output, you can use tools like `kubectl` to apply the rendered templates to your Kubernetes cluster:
    ```sh
    helm template my-release . | kubectl apply --dry-run=client -f -
    ```

This will render your templates and simulate applying them to your cluster without actually making any changes.
