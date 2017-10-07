kubectl-helm
============
[kubectl](https://kubernetes.io/docs/user-guide/kubectl-overview/)/[helm](https://helm.sh/) image for working with Kubernetes & Helm charts, based on the Docker [scratch](https://docs.docker.com/samples/library/scratch/) image.

Usage
-----
In it's most simple form, you could run for example:

```sh
docker run --rm -it zeroplusx/kubectl-helm kubectl version
docker run --rm -it zeroplusx/kubectl-helm helm version
```

You could also mount your ~/.kube and ~/.helm folders for more advanced features:

```sh
docker run --rm -it -v $HOME/.kube:/.kube -v $HOME/.helm:/.helm zeroplusx/kubectl-helm kubectl get pods
docker run --rm -it -v $HOME/.kube:/.kube -v $HOME/.helm:/.helm zeroplusx/kubectl-helm helm ls
```

Maintainers
-----------
* Sebastian Mandrean (<sebastian@0x.se>)
