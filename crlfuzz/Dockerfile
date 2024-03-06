FROM golang:alpine as build
RUN apk --no-cache add git
RUN GO111MODULE=on go install github.com/dwisiswant0/crlfuzz/cmd/crlfuzz@latest

FROM alpine:latest
COPY --from=build /go/bin/crlfuzz /bin/crlfuzz
ENV HOME /
ENTRYPOINT ["/bin/crlfuzz"]