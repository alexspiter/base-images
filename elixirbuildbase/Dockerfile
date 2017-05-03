# This is coming from https://github.com/operable/dockerfiles
FROM operable/alpine-base:0.3

ENV ERLANG_VERSION 19.1
ENV ELIXIR_VERSION 1.3.4

# Erlang
#
# Modified from
# https://github.com/bitwalker/alpine-erlang
WORKDIR /tmp/erlang-build
RUN \
    # Install Erlang/OTP deps
    apk -U add \
      openssl-dev \
      ncurses-dev \
      unixodbc-dev \
      zlib-dev && \
    # Install Erlang/OTP build deps
    apk -U add --virtual .erlang-build \
      build-base \
      perl-dev \
      gcc && \
    export ERLANG_SOURCE=otp_src_$ERLANG_VERSION && \
    wget http://erlang.org/download/$ERLANG_SOURCE.tar.gz && \
    tar -xzf $ERLANG_SOURCE.tar.gz && \
    cd $ERLANG_SOURCE && \
    export ERL_TOP=/tmp/erlang-build/$ERLANG_SOURCE && \
    export PATH=$ERL_TOP/bin:$PATH && \
    export CPPFlAGS="-D_BSD_SOURCE $CPPFLAGS" && \
    # Configure
    ./configure --prefix=/usr \
      --without-javac \
      --without-wx \
      --without-debugger \
      --without-observer \
      --without-jinterface \
      --without-common_test \
      --without-cosEvent\
      --without-cosEventDomain \
      --without-cosFileTransfer \
      --without-cosNotification \
      --without-cosProperty \
      --without-cosTime \
      --without-cosTransactions \
      --without-dialyzer \
      --without-et \
      --without-gs \
      --without-ic \
      --without-megaco \
      --without-orber \
      --without-percept \
      --without-typer \
      --enable-threads \
      --enable-shared-zlib \
      --enable-ssl=dynamic-ssl-lib \
      --enable-hipe && \
    # Build
    make -j4 && make install && \
    # Cleanup
    apk del .erlang-build && \
    rm -rf /tmp/erlang-build && \
    # Remove Erlang source code
    find /usr/lib/erlang/lib/* -type d -name src | xargs -n1 rm -Rf && \
    rm -rf /var/cache/apk/*

WORKDIR /

# Elixir
RUN wget https://github.com/elixir-lang/elixir/releases/download/v$ELIXIR_VERSION/Precompiled.zip && \
    unzip -d /usr/local Precompiled.zip && \
    rm -f /usr/local/bin/*.bat && \
    rm -f Precompiled.zip
RUN mix local.hex --force
RUN mix local.rebar --force
