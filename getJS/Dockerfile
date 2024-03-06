FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install github.com/003random/getJS@latest

FROM alpine:latest
COPY --from=build /go/bin/getJS /bin/getJS
ENV HOME /
ENTRYPOINT ["/bin/getJS"]