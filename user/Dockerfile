FROM node:20-alpine3.22
WORKDIR /opt/server
COPY *.js *.json .
RUN npm install
ENV REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/users"
CMD ["node", "server.js"]