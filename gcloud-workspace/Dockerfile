FROM google/cloud-sdk:alpine

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

ARG GIT_CRYPT_VERSION=0.6.0-r1
ARG GIT_CRYPT_SRC=https://github.com/sgerrand/alpine-pkg-git-crypt/releases/download/$GIT_CRYPT_VERSION/git-crypt-$GIT_CRYPT_VERSION.apk
ARG GIT_CRYPT_PUB_KEY_SRC=https://raw.githubusercontent.com/sgerrand/alpine-pkg-git-crypt/master/sgerrand.rsa.pub
ARG GIT_CRYPT_PUB_KEY_DEST=/etc/apk/keys/sgerrand.rsa.pub

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install *nix dependencies
RUN apk --no-cache add git curl jq docker ca-certificates && \
    apk --no-cache del wget

# Update & install gcloud dependencies
RUN gcloud components update --quiet && \
    gcloud auth configure-docker && \

    # Kubectl
    curl -#SLo $KUBE_DEST $KUBE_SRC && \
    chmod +x $KUBE_DEST && \

    # Helm
    curl -#SL $HELM_SRC | tar zxvf - && \
    mv linux-amd64/helm $HELM_DEST && rm -rf linux-amd64 && \
    chmod +x $HELM_DEST && \
    mkdir -p ~/.kube && \
    helm init -c && \

    # Skaffold
    curl -#SLo $SKAFFOLD_DEST $SKAFFOLD_SRC && \
    chmod +x $SKAFFOLD_DEST

# Add Helm repos
RUN helm repo add zeroplusx http://charts.0x.se && \
    helm repo add incubator https://kubernetes-charts-incubator.storage.googleapis.com/ && \
    helm repo update

# Install git-crypt
RUN curl -#SLo $GIT_CRYPT_PUB_KEY_DEST $GIT_CRYPT_PUB_KEY_SRC && \
    curl -#SLO $GIT_CRYPT_SRC && \
    apk --no-cache add libressl git-crypt-$GIT_CRYPT_VERSION.apk
