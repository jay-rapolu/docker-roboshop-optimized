FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY *.js *.json .
RUN npm install

FROM node:20-alpine3.21
WORKDIR /opt/server
RUN adduser -D roboshop
ENV REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
COPY --chown=roboshop:roboshop --from=builder /opt/server .
USER roboshop
CMD ["node", "server.js"]

# FROM node:20-alpine3.22
# WORKDIR /opt/server
# COPY *.js *.json .
# RUN npm install
# ENV REDIS_URL="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/users"
# CMD ["node", "server.js"]