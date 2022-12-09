FROM node:10 AS builder

WORKDIR /usr/src/app

COPY . .

RUN npm install && npm run build

FROM nginx

LABEL maintener="Tom SCHOUMACHER"

EXPOSE 80
ENV BACKEND_URL_ENV_VAR=localhost:8448

COPY nginx/ /etc/nginx/
COPY entrypoint.sh /docker-entrypoint.d/entrypoint.sh
RUN chmod +x /docker-entrypoint.d/entrypoint.sh

COPY --from=builder /usr/src/app/dist /usr/share/nginx/html/