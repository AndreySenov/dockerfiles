FROM node:lts-alpine
ENV HOME=/home/node
RUN yarn global add firebase-tools && \
    yarn cache clean && \
    firebase -V && \
    mkdir $HOME/.cache && \
    chown -R node:node $HOME
USER node
VOLUME $HOME/.cache
WORKDIR $HOME
CMD ["sh"]
