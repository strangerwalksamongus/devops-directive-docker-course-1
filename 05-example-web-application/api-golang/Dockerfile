FROM golang:1.19-alpine

WORKDIR /app

COPY . . /app/

RUN go mod download

RUN go build -o api-golang

CMD ["./api-golang"]








