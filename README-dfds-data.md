# Grafana dashboards

This repository contains dashboards for monitoring our running solutions, as well as the pipeline to
deploy more dashboards. Whenever this repository falls behind the upstream repository, make sure to
fetch it.

## Deploying Grafana

Grafana has been deployed manually using the powershell script referenced in
[the main readme](./README.md).

## Using Grafana

You must log in with the shared credentials. They are found
[here](https://eu-west-1.console.aws.amazon.com/systems-manager/parameters/grafana_admin_credentials/description?region=eu-west-1).

## Adding and deploying dashboards

Dashboards should be created/modified in the UI, then saved as JSON and put in the dashboards folder
(/grafana/dashboards). The pipeline will convert them to configmaps and they should be persisted in
k8s this way. The JSON dashboards are converted to configmaps with a
[powershell script](./grafana/Convert-JSONToConfigmap.ps1), and deployed using
[azure pipelines](./azure-pipelines.yml).