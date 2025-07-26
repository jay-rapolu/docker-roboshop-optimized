# Stage 1: Build
FROM python:3.9.23-alpine3.22 AS builder
WORKDIR /build
# Install build dependencies
RUN apk add --no-cache python3-dev build-base linux-headers pcre-dev
COPY code/requirements.txt .
RUN pip3 install --no-cache-dir --prefix=/install -r requirements.txt


# Stage 2: Final image
FROM python:3.9.23-alpine3.22
EXPOSE 8080
WORKDIR /opt/server
# Runtime dependencies only
RUN apk add --no-cache pcre curl
# Create app user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
# Copy installed Python packages from builder
COPY --from=builder /install /usr/local
# Copy application code
COPY code/payment.ini .
COPY code/*.py .
CMD ["uwsgi", "--ini", "payment.ini"]


# FROM python:3.13-alpine
# WORKDIR /opt/server
# COPY code .
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \ 
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"
# RUN apk add --no-cache gcc musl-dev linux-headers python3-dev
# RUN pip3 install -r requirements.txt
# CMD ["uwsgi", "--ini", "payment.ini"]