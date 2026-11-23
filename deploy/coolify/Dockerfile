# Builds one app from HeyPuter/everything (src/<APP>) and serves its dist/ with nginx.
FROM node:22-alpine AS build
RUN apk add --no-cache git
ARG APP
ARG UPSTREAM_REF=main
RUN test -n "$APP" || (echo "APP build arg required" && exit 1)
RUN git clone --depth 1 --branch "$UPSTREAM_REF" https://github.com/HeyPuter/everything.git /everything
WORKDIR /everything/src/${APP}
RUN npm ci
RUN npm run build

FROM nginx:1.27-alpine
COPY deploy/coolify/nginx.conf /etc/nginx/conf.d/default.conf
ARG APP
COPY --from=build /everything/src/${APP}/dist /usr/share/nginx/html
EXPOSE 80
