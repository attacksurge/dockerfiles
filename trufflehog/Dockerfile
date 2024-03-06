FROM golang:alpine as build
RUN apk --no-cache add git build-base
RUN git clone https://github.com/trufflesecurity/trufflehog.git
RUN cd trufflehog ; go install

FROM alpine:latest
RUN apk add --no-cache git
COPY --from=build /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
COPY --from=build /go/bin/trufflehog /usr/bin/trufflehog
ENV HOME /
ENTRYPOINT ["/usr/bin/trufflehog"]
