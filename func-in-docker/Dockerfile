FROM ubuntu:18.04@sha256:de774a3145f7ca4f0bd144c7d4ffb2931e06634f11529653b23eba85aef8e378

RUN set -e; \
  export DEBIAN_FRONTEND=noninteractive; \
  apt-get update; \
  apt-get install -y --no-install-recommends curl ca-certificates gpg dirmngr gpg-agent; \
  curl -sL https://deb.nodesource.com/setup_8.x | bash -; \
  curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg; \
  mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg; \
  sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-bionic-prod bionic main" > /etc/apt/sources.list.d/dotnetdev.list'; \
  apt-get update; \
  apt-get install -y nodejs azure-functions-core-tools; \
  rm -rf /var/lib/apt/lists/* /var/log/apt

RUN groupadd -r func && useradd --no-log-init -r -g func func
RUN mkdir /.azurefunctions && chown func.func /.azurefunctions
USER func:func
