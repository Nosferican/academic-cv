FROM node:22-bookworm

ARG HUGO_VERSION=0.162.0
ARG GO_VERSION=1.21.5

ENV NODE_VERSION=22
ENV HUGO_VERSION=${HUGO_VERSION}
ENV GO_VERSION=${GO_VERSION}
ENV PATH=/usr/local/go/bin:${PATH}
ENV HUGO_ENABLEGITINFO=true
ENV HUGO_LOG_I18N_WARNINGS=true
ENV HUGO_LOG_WARNINGS=true
ENV FORCE_COLOR=1
ENV PNPM_FLAGS=--no-frozen-lockfile

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates curl git tar wget \
    && rm -rf /var/lib/apt/lists/* \
    && curl -fsSL "https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz" -o /tmp/go.tar.gz \
    && tar -C /usr/local -xzf /tmp/go.tar.gz \
    && rm /tmp/go.tar.gz \
    && curl -fsSL "https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_Linux-64bit.tar.gz" -o /tmp/hugo.tar.gz \
    && tar -C /tmp -xzf /tmp/hugo.tar.gz \
    && install -m 0755 /tmp/hugo /usr/local/bin/hugo \
    && rm -f /tmp/hugo /tmp/hugo.tar.gz \
    && corepack enable \
    && npm install -g --force pnpm@10.14.0 \
    && pnpm --version
