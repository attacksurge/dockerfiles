FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install github.com/tomnomnom/hacks/anti-burl@latest

FROM alpine:latest
COPY --from=build /go/bin/anti-burl /bin/anti-burl
ENV HOME /
ENTRYPOINT ["/bin/anti-burl"]
