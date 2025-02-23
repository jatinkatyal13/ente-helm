# Ente Helm

## Introduction

Ente Helm is a project that provides Helm charts for deploying applications. Helm is a package manager for Kubernetes that allows you to define, install, and upgrade even the most complex Kubernetes applications.

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
