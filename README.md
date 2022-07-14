# Application definitions for ArgoCD

![Deployment Status](https://argocd.vivaconagua.org/api/badge?name=argocd-apps&revision=true)

This repository contains [Application](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#applications) custom resource manifests which tell [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) what to deploy on our kubernetes cluster and where to deploy it from.

**Note:** This repository does not contain kubernetes manifests for the applications themselves but instead points ArgoCD to those manifests for each application.

The structure of this repository is the following:

- **[basic-cluster/](./basic-cluster)** contains applications that configure the kubernetes cluster as a platform for our own apps.
   E.g. the [cert-manager](https://cert-manager.io/) which issues our TLS certificates is defined here.
  - Most notably, [argocd-apps.yml](basic-cluster/argocd-apps.yml) contains an application definition for this very repository. It follows the [App of Apps pattern](https://argo-cd.readthedocs.io/en/stable/operator-manual/cluster-bootstrapping/) to let ArgoCD deploy all other apps defined in this repository.

- **[vca-apps/](./vca-apps)** contains the actual applications that we are deploying on the cluster. 