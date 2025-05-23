FROM node:19.4-bullseye as build

WORKDIR /usr/src/app

COPY package*.json ./

RUN --mount=type=cache,target=/usr/src/app/.npm \
    npm set cache /usr/src/app/.nmp && \
    nom ci

COPY . . 

RUN npm run build

###
FROM nginxinc/nginx-unprivileged:1.23-alpine-perl

COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build usr/src/dist /usr/share/nginx/html

EXPOSE 8090

CMD ["npm", "run", "dev"]