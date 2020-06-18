FROM golang:1.14-alpine3.11 AS build
ENV TZ Asia/Tokyo
RUN apk update && apk add git alpine-sdk tzdata
WORKDIR /go/src/fargate-example
COPY go.mod .
COPY go.sum .
RUN go mod download
COPY . .
RUN make deps clean bin/fargate-example

FROM alpine:3.11
ENV TZ Asia/Tokyo
RUN apk --update --no-cache add ca-certificates tzdata
COPY --from=build /go/src/fargate-example/bin/fargate-example /fargate-example
CMD ["/fargate-example"]
