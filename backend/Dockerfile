# build layer
FROM golang:1.22-alpine AS builder

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

COPY . .

RUN CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -o /app/app ./cmd/api

# final layer
FROM ubuntu:22.04

RUN groupadd -r gopher && useradd -r -g gopher -s /bin/bash -m gopher

RUN mkdir /app && chown -R gopher:gopher /app

WORKDIR /app

COPY --from=builder /app .

USER gopher

EXPOSE 8081

ENTRYPOINT [ "./app" ]
