FROM golang:1.21-alpine AS builder

WORKDIR /workspace
COPY . .
RUN go build -o service ./cmd/main.go

FROM alpine:latest
WORKDIR /workspace
COPY --from=builder /workspace/service .
EXPOSE 8080
CMD ["./service"] 