FROM public.ecr.aws/docker/library/caddy:builder AS builder
 
RUN xcaddy build \
    --with github.com/caddy-dns/netlify \
    --with github.com/mholt/caddy-dynamicdns
 
FROM public.ecr.aws/docker/library/caddy:latest
 
COPY --from=builder /usr/bin/caddy /usr/bin/caddy