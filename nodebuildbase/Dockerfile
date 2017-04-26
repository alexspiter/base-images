FROM buildpack-deps:jessie

# This allows to use source in the following steps
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

ENV NVM_DIR /root
ENV NODE_VERSION v6.4.0

RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash\
    && source $NVM_DIR/nvm.sh\
    && nvm install $NODE_VERSION\
    && nvm alias default $NODE_VERSION\
    && nvm use default

ENV PATH "/root/versions/node/${NODE_VERSION}/bin:${PATH}"
# Installing with apt installs too much other packages
RUN curl -L https://www.npmjs.com/install.sh | sh