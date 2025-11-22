FROM node:lts AS builder

WORKDIR /app

COPY . .

RUN corepack enable
RUN yes | yarn set version stable
RUN yarn install
RUN yarn build


FROM caddy:2-alpine

COPY --from=builder /app/dist /srv
COPY Caddyfile /etc/caddy/Caddyfile

EXPOSE 3000
