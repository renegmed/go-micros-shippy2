FROM golang:1.11.0 as builder

WORKDIR /go/src/shippy/consignment-cli

COPY . .

#RUN go get -u github.com/golang/dep/cmd/dep
#RUN dep init && dep ensure
# RUN export GO111MODULE=on
# RUN go mod init && go mod vendor
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo .


FROM alpine:latest

RUN apk --no-cache add ca-certificates

RUN mkdir /app
WORKDIR /app
COPY consignment.json /app/consignment.json
COPY --from=builder /go/src/shippy/consignment-cli/consignment-cli .

CMD ["./consignment-cli"]
