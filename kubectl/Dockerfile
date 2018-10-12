FROM ubuntu:18.04

ENV BIN_PATH=/usr/local/bin
ENV KUBECTL_VERSION=v1.10.8

RUN apt-get update && \
    apt-get install jq -y

RUN curl -S -L -f https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl -o ${BIN_PATH}/kubectl && \
    chmod +x ${BIN_PATH}/kubectl
