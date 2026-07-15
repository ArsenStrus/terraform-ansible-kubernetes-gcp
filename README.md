# terraform-ansible-kubernetes-gcp
# ExamDevOps2

## Overview

This repository demonstrates an end-to-end DevOps workflow for provisioning infrastructure, configuring a Kubernetes environment, and deploying a containerized application on Google Cloud Platform (GCP). The project is divided into three main stages.

## Task 1 – Infrastructure Provisioning

* Provisioned GCP infrastructure using **Terraform**.
* Created reusable Terraform modules for:

  * Virtual Private Cloud (VPC)
  * Compute Engine VM (node)
  * Cloud Storage Bucket
* Implemented **GitHub Actions** workflow to automatically provision infrastructure on every push.
* Added a separate workflow for automated infrastructure destruction to simplify resource cleanup.

## Task 2 – Server Configuration

Configured the provisioned VM using **Ansible**.

The playbook performs the following actions:

* Installs required system dependencies.
* Installs and configures Docker.
* Installs Kubernetes tools:

  * kubectl
  * Minikube
  * Helm
* Creates and starts a local Kubernetes cluster with Minikube.
* Configures a `kubectl proxy` systemd service for external access.
* Includes a dedicated GitHub Actions workflow to execute the Ansible configuration automatically.

## Task 3 – Application Deployment

Created Kubernetes manifests to deploy a containerized application.

Deployment includes:

* Namespace creation.
* Kubernetes Deployment.
* Kubernetes Service.
* Automatic deployment of a Docker image from Docker Hub.
* Parameterized environment and image version using environment variables.

## Technologies Used

* Terraform
* Google Cloud Platform (GCP)
* GitHub Actions
* Ansible
* Docker
* Kubernetes
* Minikube
* Helm

## Project Workflow

1. Terraform provisions the required GCP infrastructure.
2. GitHub Actions executes the Terraform workflows.
3. Ansible configures the virtual machine and installs Kubernetes components.
4. Minikube cluster is created.
5. Kubernetes manifests deploy the Dockerized application inside the cluster.

## Security

Sensitive information such as **GCP service account credentials, project identifiers, Docker Hub credentials, and other configuration values** are not stored in the repository. All confidential data is securely managed using **GitHub Actions Secrets**, ensuring that deployment and automation workflows can run without exposing sensitive information in the source code.
