# Build stage
FROM golang:1.27-alpine@sha256:8a5910f31396cd4d89662f56c68b3ae31d374308270a1c3bd96672ee5ed43414 AS builder

WORKDIR /app

# Copy go mod files
COPY go.* ./
RUN go mod download

# Copy source code
COPY . .

# Build the binary
RUN CGO_ENABLED=0 GOOS=linux go build -o /alloy-mission-control ./cmd/server

# Runtime stage
FROM alpine:latest@sha256:25109184c71bdad752c8312a8623239686a9a2071e8825f20acb8f2198c3f659

RUN apk --no-cache add ca-certificates

WORKDIR /app

# Copy binary from builder
COPY --from=builder /alloy-mission-control .

# Create log directory for volume mount
RUN mkdir -p /var/log/alloy

EXPOSE 8080

CMD ["./alloy-mission-control"]
