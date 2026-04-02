# Systemd in Dev Spaces Demo

This repository provides helm charts using an app-of-apps methodology to configure Red Hat OpenShift to run Ansible Development Workspaces.

> [!WARNING]
> **DO NOT DEPLOY TO PRODUCTION OCP CLUSTERS** Use this at your own risk. This code may introduce breaking changes without warning, may render Red Hat OpenShift clusters inoperable, unsupported and non-functional.

## Overview

Ansible Development Workspaces are a web based development environment pre-configured for Ansible development and testing. Red Hat OpenShift Dev Spaces provides a modern IDE with relevant extensions while Red Hat OpenShift provides infrastructure for hosting testing infrastructure for tools like Molecule.

## Variants

This repository provides two helm charts for testing.

### Ansible Development Workspaces (adw)

This is the supportable helm chart that configures and deploys ADW without making changes that would prevent cluster upgrades or be unsupportable. It is focused on supportability over features.

Components deployed:

* Red Hat OpenShift Dev Spaces operator
* CheCluster configured for Ansible Development

### Ansible Development Workspaces with Nested SystemD (nested-systemd)

This is a helm chart that configures and deploys ADW with changes to the cluster that will likely make it unsupportable and unupgradable. It is focused on feature development and testing over supportability.

Components deployed:

* Red Hat OpenShift Dev Spaces operator
* CheCluster configured for Ansible Development
* Custom SecurityContextConstraints with additional capabilities and selinux context
* Custom machineconfig for enabling user cgroup capability
* Custom machineconfig for updating selinux label

## How to use

### Using Red Hat Demo Platform

* Login to Red Hat Demo Platform
* From the catalog order the "Field Sourced Content - OpenShift Base"
* In the Order form click the "Existing Gitops Repo?" checkbox
* Enter "https://github.com/jeffcpullen/systemd-in-devspaces-demo.git" in the Gitops Repo field
* Enter "main" in the GitOps Revision field
* Enter "adw" or "nested-systemd" (depending on need) in the GitOps Path
* Finish filling out the Order form and click the "Order" button to start provisioning

### Using a Red Hat OpenShift Cluster

* Login to a Red Hat OpenShift (v4.20+) cluster as a user with cluster-admin privs
* Ensure OpenShift GitOps operator is installed
* Access OpenShift GitOps console and authenticate as a user with cluster-admin privs
* Click the "+ NEW APP" icon in the top left
* Enter "field-content-demo" in the Application Name field
* Enter "default" in the Project Name field
* Check the box beside "AUTO-CREATE NAMESPACE"
* Enter "https://github.com/jeffcpullen/systemd-in-devspaces-demo.git" in the Repository URL field
* Enter "main" in the Revision field
* Enter "adw" in the Path field
* Enter "https://kubernetes.default.svc" in the Cluster URL field
* Enter "openshift-gitops" in the Namespace field
* Click "Create"
* If sync policy was set to Manual, click "Sync Apps" afterwards to apply configurations


## Contributing

This repository will likely be short lived and move to a different location in the future. Contributions / issues are welcome but may not be addressed until this code is moved to its proper location.
