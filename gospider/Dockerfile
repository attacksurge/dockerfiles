# runs inside the container but `docker run` won't work
FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install github.com/jaeles-project/gospider@latest

FROM alpine:latest
COPY --from=build /go/bin/gospider /bin/gospider
ENV HOME /
ENTRYPOINT ["gospider"]