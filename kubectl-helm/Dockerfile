FROM scratch

LABEL vendor="0+X"
LABEL maintainer="Sebastian Mandrean <sebastian@0x.se>"

ENV PATH /
ENV HOME /

# Add binaries & certs
ADD ["kubectl", "helm", "/"]
ADD ca-certificates.crt /etc/ssl/certs/

# Create folders
WORKDIR /.kube
WORKDIR /.helm
WORKDIR /

# Init helm
RUN ["/helm", "init", "-c"]

CMD ["/helm"]
