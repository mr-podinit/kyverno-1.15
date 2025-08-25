# Introduction

This repository contains all the files used during the Youtube video about Kyverno 1.15 (https://youtu.be/r9u1VSxhuAc)

> **Note:** All commands are for demonstration purposes. Adjust them according to your OS and environment.

# Setup

## First Kyverno installation

```bash
helm repo add kyverno https://kyverno.github.io/kyverno/
helm repo update
helm upgrade --install kyverno --namespace kyverno kyverno/kyverno --version 3.5.1 --values install/first-installation.yaml --create-namespace
```

## Useful commands

```bash
stern -n kyverno admission --since 10m
kubectl get validatingwebhookconfigurations.admissionregistration.k8s.io kyverno-resource-validating-webhook-cfg -o yaml
keytool -list -keystore /etc/jks-certs
# Requires Kyverno CLI installed:
kyverno test $(pwd)
```

# Additional commands to setup the environment

```bash
sudo k0s stop
sudo k0s reset
sudo k0s install controller --single
helm repo remove kyverno

sudo k0s ctr image pull docker.io/library/nginx:stable
sudo k0s ctr image pull docker.io/library/nginx:1
sudo k0s ctr image pull docker.io/library/nginx:latest
sudo k0s ctr image pull reg.kyverno.io/kyverno/kyvernopre:v1.15.1
sudo k0s ctr image pull reg.kyverno.io/kyverno/reports-controller:v1.15.1
sudo apt install kyverno stern k9s
```

# Links

* https://artifacthub.io/packages/helm/kyverno/kyverno/3.5.1
* https://kyverno.io/docs/policy-types/validating-policy/
* https://playground.kyverno.io/
* https://kyverno.io/policies/best-practices/disallow-latest-tag/disallow-latest-tag/
* https://kyverno.io/policies/other/scale-deployment-zero/scale-deployment-zero/
* https://kyverno.io/docs/introduction/admission-controllers/#webhooks


