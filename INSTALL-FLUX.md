# Flux

## Get started wth Flux

[Get started with Flux](https://docs.fluxcd.io/en/latest/tutorials/get-started.html)

```
vagrant ssh ctrlnode01
```

```
sudo snap install fluxctl --classic
kubectl create ns flux
export GHUSER=[Your GitHub Handle]
fluxctl install \
--git-user=${GHUSER} \
--git-email=${GHUSER}@users.noreply.github.com \
--git-url=git@github.com:${GHUSER}/content-gitops \
--git-path=namespaces,workloads \
--namespace=flux | kubectl apply -f -
```

Verify the Flux deployment:

```
kubectl -n flux rollout status deployment/flux
```

Obtain the Flux RSA key created by fluxctl:

```
fluxctl identity --k8s-fwd-ns flux
```

Copy off the RSA key to implement in GitHub.

## Get start with Flux using Helm

[Get started with Flux using Helm](https://docs.fluxcd.io/en/latest/tutorials/get-started-helm.html)
