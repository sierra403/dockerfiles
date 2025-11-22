FROM node:22 AS builder

WORKDIR /app

COPY . .

RUN corepack enable
RUN yes | yarn set version stable
RUN yarn install
RUN yarn build


FROM node:22-slim

WORKDIR /app

COPY --from=builder /app/.next/standalone ./
COPY --from=builder /app/.next/static ./.next/static
COPY --from=builder /app/public ./public

ENV NEXT_TELEMETRY_DISABLED=1

EXPOSE 3000

CMD ["server.js"]
