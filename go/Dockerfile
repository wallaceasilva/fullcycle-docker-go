FROM golang:1.24 AS builder

WORKDIR /usr/src/app

# COPY go.mod go.sum ./
# RUN go mod download

# COPY . .
COPY main.go .

# RUN go build -v -o /usr/local/bin/app main.go

# Compilação otimizada para um binário pequeno
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-s -w" -o app main.go


FROM scratch

COPY --from=builder /usr/src/app/app /app

CMD ["/app"]