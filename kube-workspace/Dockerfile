FROM alpine:3.9

LABEL vendor="0+X"
LABEL maintainer="Sebastian Mandrean <sebastian@0x.se>"

ARG KUBE_VERSION=1.14.7
ARG KUBE_SRC=https://storage.googleapis.com/kubernetes-release/release/v$KUBE_VERSION/bin/linux/amd64/kubectl
ARG KUBE_DEST=/usr/local/bin/kubectl

ARG HELM_VERSION=2.15.2
ARG HELM_SRC=https://storage.googleapis.com/kubernetes-helm/helm-v$HELM_VERSION-linux-amd64.tar.gz
ARG HELM_DEST=/usr/local/bin/helm

ARG SKAFFOLD_VERSION=0.41.0
ARG SKAFFOLD_SRC=https://storage.googleapis.com/skaffold/releases/v$SKAFFOLD_VERSION/skaffold-linux-amd64
ARG SKAFFOLD_DEST=/usr/local/bin/skaffold

SHELL ["/bin/sh", "-o", "pipefail", "-c"]

# Install dependencies
RUN apk --no-cache add git curl ca-certificates && \
    apk --no-cache del wget

# Install kubectl, helm & skaffold
RUN curl -#SLo $KUBE_DEST $KUBE_SRC && \
    chmod +x $KUBE_DEST && \

    curl -#SL $HELM_SRC | tar zxvf - && \
    mv linux-amd64/helm $HELM_DEST && rm -rf linux-amd64 && \
    chmod +x $HELM_DEST && \
    mkdir -p ~/.kube && \
    helm init -c && \

    curl -#SLo $SKAFFOLD_DEST $SKAFFOLD_SRC && \
    chmod +x $SKAFFOLD_DEST

# Add Helm repos
RUN helm repo add zeroplusx http://charts.0x.se && \
    helm repo add incubator https://kubernetes-charts-incubator.storage.googleapis.com/ && \
    helm repo update

CMD kubectl
