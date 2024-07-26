# syntax=docker/dockerfile:1.4
FROM directus/directus:10.10.4
USER root
RUN corepack enable \
&& corepack prepare pnpm@8.7.6 --activate \
&& chown node:node /directus

COPY ./.env.vault /directus/.env.vault

EXPOSE {{port}}
USER node
CMD : \
&& pnpm i dotenv \
&& node -r dotenv/config /directus/cli.js bootstrap \
&& node -r dotenv/config /directus/cli.js start;
