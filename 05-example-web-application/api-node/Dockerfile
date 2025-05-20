FROM node:19.6-alpine

#RUN apt update && apt install nodejs npm -y
WORKDIR /usr/src/app

ENV NODE_ENV=production

COPY package*.json ./

RUN --mount=type=cache,target=/usr/src/app/.npm \
    npm set cache /usr/src/app/.npm && \
    npm ci --only=production

USER node

COPY --chown=node:node ./src .

EXPOSE 3000

CMD ["node", "index.js"]



