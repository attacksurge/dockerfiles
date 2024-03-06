FROM golang:alpine as build
RUN apk --no-cache add git build-base libpcap-dev
RUN GO111MODULE=on go install github.com/projectdiscovery/naabu/v2/cmd/naabu@latest

FROM alpine:latest
RUN apk --no-cache add libpcap-dev
COPY --from=build /go/bin/naabu /bin/naabu
ENV HOME /
ENTRYPOINT ["/bin/naabu"]