# -- Go Builder Image --
FROM golang:1.9-alpine AS builder

ENV DEP_VERSION=0.4.1
ENV MBT_VERSION=0.21.0
ENV BIN_PATH=/usr/local/bin

RUN apk add --no-cache git curl pkgconf alpine-sdk libgit2 libgit2-dev cmake clang clang-dev make gcc g++ libc-dev linux-headers
RUN curl -fsSL -o ${BIN_PATH}/dep https://github.com/golang/dep/releases/download/v${DEP_VERSION}/dep-linux-amd64 && chmod +x ${BIN_PATH}/dep
RUN git clone --branch ${MBT_VERSION} https://github.com/mbtproject/mbt.git /go/src/mbt

WORKDIR /go/src/mbt

# https://github.com/golang/dep/blob/master/docs/FAQ.md#how-do-i-use-dep-with-docker
RUN set -ex \
  && make build

FROM golang:1.9-alpine

ENV DEP_VERSION=0.4.1
ENV HELM_VERSION=2.8.2
ENV BIN_PATH=/usr/local/bin

RUN set -ex \
  && apk add --no-cache bash ca-certificates git curl

RUN curl -fsSL -o ${BIN_PATH}/dep https://github.com/golang/dep/releases/download/v${DEP_VERSION}/dep-linux-amd64 && chmod +x ${BIN_PATH}/dep

RUN curl -L https://storage.googleapis.com/kubernetes-helm/helm-v${HELM_VERSION}-linux-amd64.tar.gz | tar -xzC ${BIN_PATH}/ && \
	mv $BIN_PATH/linux-amd64/helm $BIN_PATH/ && \
    rm -rf $BIN_PATH/linux-amd64/

RUN go get github.com/mitchellh/gox
COPY --from=builder /go/src/mbt/build/mbt_linux_x86_64 $GOPATH/bin/mbt

CMD bash
