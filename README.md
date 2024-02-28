# fluxcd
POC for fluxcd

## Documentation

As with every guide, we start with the documentation </br>
The [Core Concepts](https://fluxcd.io/flux/concepts/) is a good place to start. </br>

We begin by following the steps under the [bootstrap](https://fluxcd.io/flux/installation/#bootstrap) section for GitHub </br>

We'll need to generate a [personal access token (PAT)](https://github.com/settings/tokens/new) that can create repositories by checking all permissions under `repo`.  </br>

Once we have a token, we can set it: 

```
export GITHUB_TOKEN=<your-token>
```

Then we can bootstrap it using the GitHub bootstrap method

```
flux bootstrap github \
  --token-auth \
  --owner=lokendrachhetri9 \
  --repository=fluxcd \
  --path=repositories/infra-repo/clusters/dev-cluster \
  --personal \
  --branch main

# flux manages itself using GitOps objects:
kubectl -n flux-system get GitRepository
kubectl -n flux-system get Kustomization
```