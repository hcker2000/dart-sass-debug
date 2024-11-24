FROM ubuntu:22.04

WORKDIR /usr/local

COPY ./docker-entrypoint.sh /

RUN apt-get -y update \
 && apt-get -y install \
    ca-certificates \
    curl \
 && rm -rf /var/lib/apt/lists/*
 
RUN chmod +x /docker-entrypoint.sh

# Replace the SASS_VERSION with the version you want to install
ARG SASS_VERSION=1.81.0
ARG SASS_URL="https://github.com/sass/dart-sass/releases/download/${SASS_VERSION}/dart-sass-${SASS_VERSION}-linux-x64.tar.gz"

RUN curl -OL $SASS_URL

# Extract the release (if it's an archive)
RUN tar -xzf dart-sass-${SASS_VERSION}-linux-x64.tar.gz

# Clean up downloaded files (optional)
RUN rm -rf dart-sass-${SASS_VERSION}-linux-x64.tar.gz

ENV PATH=$PATH:/usr/local/dart-sass

ENTRYPOINT ["/docker-entrypoint.sh"]
