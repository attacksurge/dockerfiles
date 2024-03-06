# need a target to test, confident it works
FROM golang:alpine as build
RUN apk --no-cache add git build-base
RUN GO111MODULE=on go install github.com/jaeles-project/jaeles@latest

FROM alpine:latest
COPY --from=build /go/bin/jaeles /bin/jaeles
RUN /bin/jaeles config init
#ENTRYPOINT ["/bin/jaeles"]