FROM golang:1.22-alpine AS builder

WORKDIR /usr/src/app

COPY . .

RUN go mod download && go build -o product-catalog ./

FROM alpine AS release

WORKDIR /usr/src/app

COPY ./products ./products

COPY --from=builder /usr/src/app/product-catalog ./

EXPOSE 8080
ENTRYPOINT ["./product-catalog"]
