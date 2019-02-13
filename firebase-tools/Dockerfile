FROM node:lts-alpine
ARG VERSION
ARG VCS_REF
LABEL org.label-schema.schema-version = "1.0" \
      org.label-schema.name = "firebase-tools" \
      org.label-schema.version = $VERSION \
      org.label-schema.description = "Firebase CLI on the NodeJS LTS image" \
      org.label-schema.url = "https://firebase.google.com/" \
      org.label-schema.vcs-url = "https://github.com/AndreySenov/dockerfiles/" \
      org.label-schema.vcs-ref = $VCS_REF
ENV FIREBASE_TOOLS_VERSION=$VERSION
ENV HOME=/home/node
RUN yarn global add firebase-tools@VERSION && \
    yarn cache clean && \
    firebase -V && \
    mkdir $HOME/.cache && \
    chown -R node:node $HOME
USER node
VOLUME $HOME/.cache
WORKDIR $HOME
CMD ["sh"]
