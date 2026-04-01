# Ansible Development Workspaces (ADW) - App of Apps

This helm chart configures and deploys everything necessary to run Ansible Developer Workspaces on Red Hat OpenShift v4.20+.

> [!NOTE]
> This helm chart is being used for testing and development and may have breaking changes without any notice. Do not assume any support or stability for this helm chart.

## Whats included

This helm chart depends on a fresh Red Hat OpenShift cluster (v4.20+). The following changes are made

* Installs Red Hat OpenShift Dev Spaces Operator
* Configures a CheCluster object preconfigured for Ansible Development
