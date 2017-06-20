FROM alpine:3.6
ENV HELM_VERSION 2.3.1
RUN apk --update add py-pip bash curl tar && \
  pip install awscli
RUN curl -O https://storage.googleapis.com/kubernetes-helm/helm-v${HELM_VERSION}-linux-amd64.tar.gz && \
  tar -xvf helm-v${HELM_VERSION}-linux-amd64.tar.gz && \
  cp -rfp linux-amd64/helm /usr/local/bin/ && \
  rm -rf linux-amd64*
