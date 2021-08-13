FROM caddy:builder-alpine AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/dnspod \
    --with github.com/abiosoft/caddy-exec \
    --with github.com/mholt/caddy-webdav \
    --with github.com/RussellLuo/caddy-ext/ratelimit \
    --with github.com/lucaslorentz/caddy-docker-proxy \
    --with github.com/mholt/caddy-l4 \
    --with github.com/WingLim/caddy-webhook \
    --with github.com/ueffel/caddy-brotli \
    --with github.com/vbaldinof/caddy-supervisor

FROM caddy:alpine

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
