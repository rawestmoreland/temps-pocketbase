FROM golang:1.18 AS builder

RUN mkdir /app
ADD . /app
WORKDIR /app

RUN CGO_ENABLED=0 GOOS=linux go build -o my_app main.go

FROM alpine:latest AS production
COPY --from=builder /app .
CMD ["/my_app", "serve", "--http", "0.0.0.0:5000",  "--dir=/pb_data"]