FROM ruby:2.3

ENV PHANTOMJS_VERSION 2.1.1

RUN apt-get update && apt-get install -y nodejs postgresql-client
RUN wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 \
    && bunzip2 phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar.bz2 \
    && tar xvf phantomjs-$PHANTOMJS_VERSION-linux-x86_64.tar \
    && cp /phantomjs-$PHANTOMJS_VERSION-linux-x86_64/bin/phantomjs /usr/bin/phantomjs
