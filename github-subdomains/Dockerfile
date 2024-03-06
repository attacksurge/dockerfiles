FROM golang:alpine as build
RUN apk --no-cache add git
RUN GO111MODULE=off go get -u github.com/gwen001/github-subdomains

FROM alpine:latest
COPY --from=build /go/bin/github-subdomains /bin/github-subdomains
ENV HOME /
ENTRYPOINT ["/bin/github-subdomains"]