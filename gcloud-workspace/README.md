gcloud-workspace
================
Google Cloud workspace image for authenticating and working with GCP resources, based on [google/cloud-sdk:alpine](https://hub.docker.com/r/google/cloud-sdk/).

Contains CLI tools such as [gcloud](https://cloud.google.com/sdk/gcloud/), [gsutil](https://cloud.google.com/storage/docs/gsutil), [docker](https://docs.docker.com/engine/reference/commandline/cli/), [kubectl](https://kubernetes.io/docs/user-guide/kubectl-overview/), [helm](https://helm.sh/), [skaffold](https://github.com/GoogleContainerTools/skaffold), [jq](https://stedolan.github.io/jq/), [git-crypt](https://github.com/AGWA/git-crypt), [curl](https://curl.haxx.se/) and others.

Usage
-----
In it's most simple form, you could run for example:

```sh
docker run --rm zeroplusx/gcloud-workspace gcloud version
docker run --rm zeroplusx/gcloud-workspace docker version
docker run --rm zeroplusx/gcloud-workspace kubectl version
docker run --rm zeroplusx/gcloud-workspace helm version
docker run --rm zeroplusx/gcloud-workspace skaffold version
docker run --rm zeroplusx/gcloud-workspace git-crypt version
docker run --rm zeroplusx/gcloud-workspace curl --version
```

You could also mount a service account key and authenticate for more advanced features:

```sh
docker run --rm \
	-v /path/to/service-account-key.json:/home/auth.json

	zeroplusx/gcloud-workspace gcloud auth activate-service-account --key-file /home/auth.json && \
		gcloud container clusters get-credentials YOUR_GKE_CLUSTER --project YOUR_GCP_PROJECT && \
		gcloud container clusters list
```

Maintainers
-----------
* Sebastian Mandrean (<sebastian@0x.se>)
