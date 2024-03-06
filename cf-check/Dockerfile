FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install github.com/dwisiswant0/cf-check@latest

FROM alpine:latest
COPY --from=build /go/bin/cf-check /bin/cf-check
ENV HOME /
ENTRYPOINT ["/bin/cf-check"]
