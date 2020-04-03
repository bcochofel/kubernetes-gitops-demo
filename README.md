# kubernetes-gitops-demo

GitOps demo with Flux and Fabrikate

# Prerequisites

You'll need the following binaries on your path:

- helm
- fab
- fluxctl

# Add subcomponents

To add subcomponents check the fab add help:

```bash
fab add --help
```

e.g., to add prometheus-operator:

```bash
fab add prometheus-operator --source https://github.com/helm/charts \
  --path stable/prometheus-operator --type helm --branch master
```

to create a custom configuration for prometheus-operator in the demo
environment:

```bash
fab set --environment demo --subcomponent prometheus-operator \
  fullnameOverride="prometheus-k8s"
```

# Install and generate manifests

To install the hem charts and generate the manifests:

```bash
fab install
fab generate demo
```

This will generate the manifests on the folder ```./generated/demo/```.
This will become the folder that ```flux``` checks for new/update manifests.

# References

- [GitOps](https://www.weave.works/blog/gitops-operations-by-pull-request)
- [Flux](https://github.com/fluxcd/flux)
- [Fabrikate](https://github.com/microsoft/fabrikate)
