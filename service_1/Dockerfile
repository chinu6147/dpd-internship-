# ---- Build Stage ----
FROM golang:1.24.4-alpine AS builder
WORKDIR /app
COPY . .
RUN go build -o service_1 .

# ---- Run Stage ----
FROM alpine:latest
WORKDIR /app
COPY --from=builder /app/service_1 .
EXPOSE 8001
CMD ["./service_1"]