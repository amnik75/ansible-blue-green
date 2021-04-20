# TODO v3.0.0
FROM golang:alpine
ENV HTTP_PROXY="http://172.17.0.1:8118"
ENV HTTPS_PROXY="http://172.17.0.1:8118"
RUN apk add --no-cache git
WORKDIR /app/myapp
COPY go.mod .
COPY go.sum .
RUN go mod download
COPY . .
RUN go build -o ./out/myapp .
EXPOSE 3000
CMD ["./out/myapp"]

