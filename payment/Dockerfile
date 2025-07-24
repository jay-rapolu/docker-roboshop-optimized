FROM python:3.13-alpine
WORKDIR /opt/server
COPY code .
ENV CART_HOST="cart" \
    CART_PORT="8080" \ 
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
RUN apk add --no-cache gcc musl-dev linux-headers python3-dev
RUN pip3 install -r requirements.txt
CMD ["uwsgi", "--ini", "payment.ini"]