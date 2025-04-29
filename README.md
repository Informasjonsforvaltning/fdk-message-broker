# FDK message broker

This repository contains GitHub Actions workflows for deploying a rabbitMQ instance using a shared Helm chart from the [`helm-chart`](https://github.com/Informasjonsforvaltning/helm-chart) repository.

## Purpose

The main goal of this repository is to manage environment-specific rabbitMQ deployments (staging, demo & prod) for the FDK ecosystem using reusable Helm charts. <br>
All configuration and logic for deployment resides in GitHub Actions, while the Helm chart itself is maintained in a centralized location.

> [!Note]
> This repository is not intended for direct use. It is a wrapper around the Helm chart repository and is designed to be used in conjunction with it.

> [!Warning]
> The rabbitMQ instance is gradually being replaced with Kafka, and this repository will be archived when all services have been migrated to Kafka. See [fdk-event-streaming-service](https://github.com/Informasjonsforvaltning/fdk-event-streaming-service).

## Repository Structure

```
.
├── .github/
    └── workflows/
        ├── deploy-staging.yaml       # GitHub Actions workflow to deploy MongoDB to staging
        └── deploy-prod&demo.yaml     # GitHub Actions workflow to deploy MongoDB to prod & demo
```

## Deployment

The deployment is triggered via GitHub Actions when changes are pushed to the repository, or by manual triggers.
For running one of the workflows, navigate to the `Actions` tab in the GitHub repository and select the desired workflow (`Deploy to staging` or `Deploy to production & demo`).

Secrets required for deployment (e.g., GCP service account keys) are stored as GitHub secrets in the repository settings.

## Helm Chart Source

The rabbitMQ Helm chart used in this repository is maintained in:

🔗 [`Informasjonsforvaltning/helm-chart`](https://github.com/Informasjonsforvaltning/helm-chart/helm-chart-sources/rabbitmq)

Any updates or changes to the rabbitMQ configuration must be done there.

## Requirements

- Access to GitHub Actions.
- Required secrets configured.

## Updating the Chart Version

The workflows will automatically pull the latest version of the chart in the helm-chart repo and deploy it to the specified environment.
