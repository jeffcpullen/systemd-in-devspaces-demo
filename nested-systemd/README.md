# Helm Example - App of Apps

This helm chart configures and deploys everything necessary to run Ansible Developer Workspaces on Red Hat OpenShift v4.20+. It applies unsupported changes to the OpenShift nodes to enable nesting containers that include systemd. This allows for container based Ansible testing that includes starting and stopping services.

[!WARNING]
The fixes included in this configuration are *not supported* and will prevent the OpenShift cluster from upgrading. This should not be applied to production OpenShift clusters. It is strictly for testing and development. *DO NOT RUN AGAINST OPENSHIFT CLUSTERS THAT NEED CONTINUED SUPPORT.*
