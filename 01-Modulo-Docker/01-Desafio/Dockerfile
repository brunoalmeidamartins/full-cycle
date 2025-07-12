FROM golang:1.24-alpine AS builder

LABEL authors="brunoalmeidamartins"

ENV CGO_ENABLED=0 \
    GOOS=linux \
    GOARCH=amd64

WORKDIR /app

COPY hello_world.go .

RUN go build -trimpath -ldflags="-s -w" -o hello_world hello_world.go

FROM scratch

COPY --from=builder /app/hello_world /hello_world

ENTRYPOINT ["/hello_world"]