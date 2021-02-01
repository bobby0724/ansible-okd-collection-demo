# OKD Ansible collection demo

This repo contains a variety of demos of the functionality in the community.okd Ansible collection

The `demo.yml` playbook is the entrypoint, and will run all the code in the repo. It imports several task files, detailed below, and also makes use of the `openshift` inventory plugin to add all pods in the cluster to the Ansible inventory as targetable hosts.

`imagestreams.yml` will demonstrate how the module will avoid updating the image field for Deployments and DeploymentConfigs when updating the PodSpec when an ImageStream is referenced. This will prevent the resource from being changed unnecessarily, and will also avoid infinite reconciliation loops when used by an operator.

`templates.yml` demonstrates how the `openshift_process` module can be used to render OpenShift templates and create the resulting resources.

`route.yml` demonstrates how a variety of routes can easily be created with the `openshift_route` module, rather than needing to craft the definitions by hand.

`auth.yml` demonstrates how the `openshift_auth` module interacts with the OpenShift OAuth server, allowing access to clusters with just username and password.

In order to run it you must have the following Python modules installed:
- `openshift`
- `ansible`

As well as the following Ansible collections:
- community.okd


The following commands will work to install them:

```bash
$ pip install --user ansible openshift
$ ansible-galaxy collection install community.okd
```

For the inventory plugin examples, you will also need the `oc` binary.
