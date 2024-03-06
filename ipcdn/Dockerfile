FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install -v github.com/six2dez/ipcdn@latest

FROM alpine:latest
COPY --from=build /go/bin/ipcdn /bin/ipcdn
ENV HOME /
ENTRYPOINT ["/bin/sh"]
