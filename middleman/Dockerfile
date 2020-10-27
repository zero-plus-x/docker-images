FROM ruby:2.6-alpine3.11

LABEL vendor="0+X"
LABEL maintainer="Sebastian Mandrean <sebastian@0x.se>"

WORKDIR /src

# Install dependencies
RUN apk --no-cache add \
		git \
		make \
		curl \
		curl-dev \
		nodejs \
		ruby-dev \
		build-base && \
	apk --no-cache del wget

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 4567
