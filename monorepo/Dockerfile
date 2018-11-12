FROM golang:1.11

ENV DEP_VERSION=0.5.0
ENV MBT_VERSION=0.21.0

RUN set -ex \
  && apt-get update \
  && apt-get install bash git curl libssl libssl-dev -y

RUN curl -fsSL -o /usr/local/bin/dep https://github.com/golang/dep/releases/download/v${DEP_VERSION}/dep-linux-amd64 && chmod +x /usr/local/bin/dep

RUN curl -L -o /usr/local/bin/mbt https://bintray.com/buddyspike/bin/download_file?file_path=mbt_linux_x86_64%2F${MBT_VERSION}%2F${MBT_VERSION}%2Fmbt_linux_x86_64 && \
chmod +x /usr/local/bin/mbt

RUN go get github.com/mitchellh/gox

CMD bash
