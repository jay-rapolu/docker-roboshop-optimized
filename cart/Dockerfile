FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY *.js *.json .
RUN npm install

FROM node:20-alpine3.21
WORKDIR /opt/server
RUN adduser -D roboshop
RUN apk add curl
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
COPY --chown=roboshop:roboshop --from=builder /opt/server .
USER roboshop
CMD ["node", "server.js"]

# FROM node:20-alpine3.22
# WORKDIR /opt/server
# COPY *.js *.json .
# RUN npm install
# ENV REDIS_HOST="redis" \
#     CATALOGUE_HOST="catalogue" \
#     CATALOGUE_PORT="8080"
# CMD ["node", "server.js"]