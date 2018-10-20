FROM google/cloud-sdk:alpine

LABEL vendor="0+X"
LABEL maintainer="Sebastian Mandrean <sebastian@0x.se>"

ENV HELM_VERSION 2.11.0
ENV HELM_SRC https://storage.googleapis.com/kubernetes-helm/helm-v$HELM_VERSION-linux-amd64.tar.gz
ENV HELM_DEST /usr/local/bin/helm

ENV SKAFFOLD_VERSION v0.16.0
ENV SKAFFOLD_SRC https://storage.googleapis.com/skaffold/releases/$SKAFFOLD_VERSION/skaffold-linux-amd64
ENV SKAFFOLD_DEST /usr/local/bin/skaffold

# Install dependencies
RUN apk --no-cache add git curl jq docker && \
	apk --no-cache del wget && \
	gcloud components update --quiet && \
	gcloud components install kubectl --quiet

# Install helm
RUN curl -#SL $HELM_SRC | tar zxvf - && \
	mv linux-amd64/helm $HELM_DEST && rm -rf linux-amd64 && \
	chmod +x $HELM_DEST && \
	mkdir -p ~/.kube && \
	helm init -c

# Install skaffold
RUN curl -#SLo $SKAFFOLD_DEST $SKAFFOLD_SRC && \
	chmod +x $SKAFFOLD_DEST
