FROM golang:1.9 as builder

WORKDIR /go/src/micro-go/consignment-cli

COPY . .

RUN go get -u github.com/golang/dep/cmd/dep

RUN echo $GOPATH
RUN dep init && dep ensure

FROM alpine:latest

RUN apk --no-cache add ca-certificates

COPY --from=builder /home/olli/repos/micro-go/consignment-cli .

CMD ["./consignment-cli"]

