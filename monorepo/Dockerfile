FROM golang:1.9-alpine

ENV DEP_VERSION=0.4.1
ENV MBT_VERSION=0.21.0
ENV HELM_VERSION=2.8.2
ENV BIN_PATH=/usr/local/bin

RUN set -ex \
  && apk add --no-cache bash ca-certificates git curl

RUN curl -fsSL -o ${BIN_PATH}/dep https://github.com/golang/dep/releases/download/v${DEP_VERSION}/dep-linux-amd64 && chmod +x ${BIN_PATH}/dep

RUN curl -L https://storage.googleapis.com/kubernetes-helm/helm-v${HELM_VERSION}-linux-amd64.tar.gz | tar -xzC ${BIN_PATH}/ && \
	mv $BIN_PATH/linux-amd64/helm $BIN_PATH/ && \
    rm -rf $BIN_PATH/linux-amd64/

RUN curl -L -o $GOPATH/bin/mbt https://bintray.com/buddyspike/bin/download_file?file_path=mbt_linux_x86_64%2F${MBT_VERSION}%2F${MBT_VERSION}%2Fmbt_linux_x86_64 && \
chmod +x $GOPATH/bin/mbt

CMD bash
