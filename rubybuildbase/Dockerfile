FROM quay.io/honestbee/alpinebase:3.6

ENV RUBY_VERSION 2.4.1-r3
ENV BUNDLER_VERSION 1.15.0-r0

RUN apk -U add \
    ruby=$RUBY_VERSION \
    ruby-dev=$RUBY_VERSION \
    ruby-json=$RUBY_VERSION \
    ruby-bundler=$BUNDLER_VERSION \
    ruby-irb=$RUBY_VERSION \
    libpq \
    build-base \
    postgresql-dev \
    libxml2-dev \
    libxslt \
    qt \
    xvfb \
    libffi-dev \
    ruby-bigdecimal \
    imagemagick imagemagick-dev \
    graphviz \
    nodejs
