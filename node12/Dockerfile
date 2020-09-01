FROM node:12

ENV CHROME_BIN /usr/bin/google-chrome-stable

RUN apt-get update && \
      apt-get install -y --force-yes \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        make \
        libssl-dev \
        libghc-zlib-dev \
        libcurl4-gnutls-dev \
        libexpat1-dev \
        gettext \
        --no-install-recommends libx11-xcb1 \
        && \
      curl -sSL https://dl.google.com/linux/linux_signing_key.pub | apt-key add - && \
      echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google-chrome.list && \
      apt-get update && apt-get install -y --force-yes google-chrome-stable  --no-install-recommends && \
      rm -rf /var/lib/apt/lists/* && \
      groupadd -r chrome && \
      useradd -r -g chrome -G audio,video chrome && \
      mkdir -p /home/chrome && \
      chown -R chrome:chrome /home/chrome && \
      chown -R chrome:chrome /opt/google/chrome && \
      wget https://github.com/git/git/archive/v2.18.0.tar.gz -O git.tar.gz && \
      tar -xf git.tar.gz && \
      cd git-* && \
      make prefix=/usr/local all && \
      make prefix=/usr/local install
