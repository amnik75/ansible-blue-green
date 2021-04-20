# TODO v3.0.0
FROM golang:alpine
RUN apk add --no-cache git
WORKDIR /app/myapp
COPY go.mod .
COPY go.sum .
RUN go mod download
COPY . .
RUN go build -o ./out/myapp .
EXPOSE 3000
CMD ["./out/myapp"]

