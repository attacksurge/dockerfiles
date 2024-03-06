FROM golang:alpine as build
RUN apk --no-cache add git
RUN GO111MODULE=off go get -u github.com/gwen001/github-endpoints

FROM alpine:latest
COPY --from=build /go/bin/github-endpoints /bin/github-endpoints
ENV HOME /
ENTRYPOINT ["/bin/github-endpoints"]