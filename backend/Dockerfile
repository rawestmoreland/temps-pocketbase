FROM golang:1.18 AS builder

RUN mkdir /app
ADD . /app
WORKDIR /app

RUN cd backend && CGO_ENABLED=0 GOOS=linux go build -o my_app main.go

FROM alpine:latest AS production
COPY --from=builder /app .
CMD ["backend/my_app", "serve", "--http", "0.0.0.0:5000",  "--dir=/backend/pb_data"]