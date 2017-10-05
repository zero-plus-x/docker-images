FROM node:8-alpine

LABEL vendor="0+X"
LABEL maintainer="Sebastian Mandrean <sebastian@0x.se>"

WORKDIR /app

# Install dependencies
RUN echo "@community http://dl-4.alpinelinux.org/alpine/edge/community/" >> /etc/apk/repositories && \
	apk --no-cache add \
		git \
		make \
		curl \
		yarn@community && \
	apk --no-cache del wget

ADD entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 4567
