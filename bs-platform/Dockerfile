FROM node:lts-alpine
ARG VERSION
RUN apk add g++ make python && \
    yarn global add bs-platform@${VERSION}

FROM node:lts-alpine
ARG BUILD_DATE
ARG VERSION
ARG VCS_REF
LABEL org.label-schema.schema-version = "1.0"
LABEL org.label-schema.name = "bs-platform"
LABEL org.label-schema.version = ${VERSION}
LABEL org.label-schema.build-date = ${BUILD_DATE}
LABEL org.label-schema.description = "BuckleScript and Reason on the NodeJS LTS image"
LABEL org.label-schema.url = "https://github.com/bucklescript/bucklescript/"
LABEL org.label-schema.vcs-url = "https://github.com/AndreySenov/dockerfiles/"
LABEL org.label-schema.vcs-ref = ${VCS_REF}
COPY --from=0 /usr/local/share/.config/yarn/global /usr/local/share/.config/yarn/global
ENV BS_PLATFORM_VERSION=${VERSION}
ENV HOME=/home/node
RUN cd /usr/local && \
    ln -s ../share/.config/yarn/global/node_modules/.bin/bsb bin/bsb && \
    ln -s ../share/.config/yarn/global/node_modules/.bin/bsc bin/bsc && \
    ln -s ../share/.config/yarn/global/node_modules/.bin/bsrefmt bin/bsrefmt && \
    bsb -v && \
    bsc -v && \
    mkdir $HOME/.cache && \
    chown -R node:node $HOME
USER node
VOLUME $HOME/.cache
WORKDIR $HOME
CMD ["sh"]
