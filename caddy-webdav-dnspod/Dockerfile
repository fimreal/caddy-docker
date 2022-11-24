FROM caddy:builder-alpine AS builder

RUN xcaddy build \
  --with github.com/RussellLuo/caddy-ext/ratelimit \
  --with github.com/caddy-dns/dnspod \
  --with github.com/WingLim/caddy-webhook \
  --with github.com/ueffel/caddy-brotli \
  --with github.com/mholt/caddy-webdav

FROM caddy:alpine

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
ADD ./Caddyfile /etc/caddy/Caddyfile
WORKDIR /caddyroot

