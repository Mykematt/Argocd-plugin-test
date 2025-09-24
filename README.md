# ArgoCD Plugin Test

Test repository for comprehensive ArgoCD Buildkite plugin testing.

## Overview

This repository contains test scenarios for the ArgoCD Buildkite plugin, including:

- ✅ **Successful deployments** with log collection and artifacts
- 💥 **Auto-rollback testing** on deployment failures  
- 🚫 **Manual rollback scenarios** with health checks disabled
- 🔔 **Multi-channel notifications** (Slack, Email)
- 📋 **Comprehensive logging** and artifact collection

## Structure

```
├── .buildkite/
│   └── pipeline.yml              # Buildkite pipeline configuration
├── argocd-application.yaml       # ArgoCD app for good deployment
├── argocd-application-broken.yaml # ArgoCD app for broken deployment
├── good-app/                     # Working nginx deployment
│   ├── namespace.yaml
│   ├── deployment.yaml           # nginx:1.25 (working)
│   ├── service.yaml
│   └── kustomization.yaml
└── bad-app/                      # Broken nginx deployment
    ├── deployment.yaml           # nginx:invalid-tag (broken)
    └── kustomization.yaml
```

## Test Pipeline

The pipeline runs 4 comprehensive test steps:

1. **🚀 Deploy Baseline** - Establishes working deployment
2. **💥 Deploy Broken (Auto-Rollback)** - Tests automatic rollback on failure
3. **🚫 Deploy Broken (No Auto-Rollback)** - Tests failure without auto-rollback
4. **🔄 Manual Rollback** - Tests manual rollback with decision blocks

## Features Tested

- [x] ArgoCD application deployment
- [x] Health monitoring and checks
- [x] Automatic rollback on failures
- [x] Manual rollback with user intervention
- [x] Log collection and artifact upload
- [x] Multi-channel notifications
- [x] Buildkite annotations
- [x] Metadata tracking

## Usage

1. Connect this repository to Buildkite
2. Configure environment variables:
   - `SLACK_CHANNEL` - Slack channel for notifications
   - `NOTIFICATION_EMAIL` - Email for notifications
3. Run the pipeline to test all ArgoCD plugin features

## Plugin

Uses: `github.com/Mykematt/argocd-deployment-buildkite-plugin#main`
