FROM quay.io/honestbee/alpinebase:3.4

ENV RUBY_VERSION 2.3.1-r0
ENV BUNDLER_VERSION 1.12.5-r0

RUN apk -U add \
    ruby=$RUBY_VERSION \
    ruby-dev=$RUBY_VERSION \
    ruby-json=$RUBY_VERSION \
    ruby-bundler=$BUNDLER_VERSION \
    build-base
