# FROM node:20-alpine3.22
# WORKDIR /opt/server
# COPY *.js *.json .
# RUN npm install
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]

FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY *.js *.json .
RUN npm install

FROM node:20-alpine3.21
WORKDIR /opt/server
COPY --from=builder /opt/server .
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node", "server.js"]