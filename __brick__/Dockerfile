# syntax=docker/dockerfile:1.4
FROM directus/directus:11.14.1
ENV COREPACK_ENABLE_DOWNLOAD_PROMPT=0

USER root
RUN corepack enable \
&& corepack prepare pnpm@10.28.1 --activate \
&& chown node:node /directus

COPY ./.env.vault /directus/.env.vault

EXPOSE {{port}}
USER node
CMD : \
&& pnpm i dotenv \
&& node -r dotenv/config /directus/cli.js bootstrap \
&& node -r dotenv/config /directus/cli.js start;
