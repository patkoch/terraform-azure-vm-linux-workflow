# Terraform Azure Virtual Machine Linux Workflow

## Overview

This repository contains a GitHub Actions workflow for managing Linux Virtual Machines in Azure using Terraform. The workflow implements a complete CI/CD pipeline with appropriate security measures and approval gates.

## Current state of the workflow execution:

[![Deploy or Destroy Linux Virtual Machine](https://github.com/patkoch/terraform-azure-vm-linux-workflow/actions/workflows/linux-virtual-machine.yml/badge.svg)](https://github.com/patkoch/terraform-azure-vm-linux-workflow/actions/workflows/linux-virtual-machine.yml)


## Workflow Structure

Triggers
  * Manual Trigger (workflow_dispatch)
        Choice between deploy and destroy
  * Pull Request Trigger
    Target branches: main, feature/**

1. PR Verification

Automated checks for pull requests including:

  * Terraform format validation
  * Infrastructure code initialization
  * Configuration validation
  * TFLint analysis
  * Plan generation
  * Automated PR comments with results

2. Verification

Pre-deployment checks:

  * Required secrets validation
  * Azure storage account verification
  * Azure connectivity testing

3. Plan Generation

Infrastructure planning:

  * Terraform initialization
  * Plan creation
  * Artifact storage
  * Plan documentation

4. Apply (Protected)

Controlled deployment:

  * Requires manual approval via GitHub Environment
  * Uses saved plan from previous stage

Ensures reviewed changes only

## Security

Required Secrets:

  * CLIENT_ID
  * SSH_PUBLIC_KEY
  * SUBSCRIPTION_ID
  * TENANT_ID
  * VIRTUAL_MACHINE_ADMIN_PASSWORD

Protection Measures

  * Environment protection rules
  * Required reviewers for deployments
  * Encrypted state management
  * Azure RBAC integration
  * Secure secret handling

## Usage

Prerequisites:

 1. Azure Subscription
 2. GitHub Repository
 3. Configured GitHub Secrets
 4. Azure Storage Account for Terraform State


Deployment:

 1. Create a new feature branch
 2. Make infrastructure changes
 3. Create pull request
 4. Wait for automated checks
 5. Get PR approval
 6. Merge to main
 7. Trigger manual deployment
 8. Approve in production environment

## Best Practices

 * Always review Terraform plans
 * Use feature branches for changes
 * Ensure proper secret management
 * Follow PR review process
 * Monitor deployment status

---
## Attribution
This README was generated with the assistance of GitHub Copilot on June 15, 2025.