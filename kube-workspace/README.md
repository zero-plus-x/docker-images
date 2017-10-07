kube-workspace
==============
Kubernetes workspace image containing [kubectl](https://kubernetes.io/docs/user-guide/kubectl-overview/), [helm](https://helm.sh/), curl etc. Based on [Alpine](https://docs.docker.com/samples/library/alpine/) Linux.

Usage
-----
In it's most simple form, you could run for example:

```sh
docker run --rm -it zeroplusx/kube-workspace kubectl version
docker run --rm -it zeroplusx/kube-workspace helm version
docker run --rm -it zeroplusx/kube-workspace curl --version
```

You could also mount your ~/.kube and ~/.helm folders for more advanced features:

```sh
docker run --rm -it -v $HOME/.kube:/.kube -v $HOME/.helm:/.helm zeroplusx/kube-workspace kubectl get pods
docker run --rm -it -v $HOME/.kube:/.kube -v $HOME/.helm:/.helm zeroplusx/kube-workspace helm ls
```

Maintainers
-----------
* Sebastian Mandrean (<sebastian@0x.se>)
