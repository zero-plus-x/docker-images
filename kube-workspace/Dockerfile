FROM alpine:3.6

LABEL vendor="0+X"
LABEL maintainer="Sebastian Mandrean <sebastian@0x.se>"

ENV KUBE_VERSION 1.7.8
ENV KUBE_SRC https://storage.googleapis.com/kubernetes-release/release/v$KUBE_VERSION/bin/linux/amd64/kubectl
ENV KUBE_DEST /usr/local/bin/kubectl

ENV HELM_VERSION 2.6.2
ENV HELM_SRC https://storage.googleapis.com/kubernetes-helm/helm-v$HELM_VERSION-linux-amd64.tar.gz
ENV HELM_DEST /usr/local/bin/helm

# Install dependencies
RUN apk --no-cache add git curl ca-certificates && \
	apk --no-cache del wget

# Install kubectl & helm
RUN curl -#SL -o $KUBE_DEST $KUBE_SRC && \
	chmod +x $KUBE_DEST && \
	curl -#SL $HELM_SRC | tar zxvf - && \
	mv linux-amd64/helm $HELM_DEST && rm -rf linux-amd64 && \
	chmod +x $HELM_DEST && \
	mkdir -p ~/.kube && \
	helm init -c

# Add Helm repos
RUN helm repo add zeroplusx http://charts.0x.se && \
    helm repo add incubator https://kubernetes-charts-incubator.storage.googleapis.com/ && \
    helm repo update

CMD kubectl
