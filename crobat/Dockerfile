FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install github.com/cgboal/sonarsearch/cmd/crobat@latest

FROM alpine:latest
COPY --from=build /go/bin/crobat /bin/crobat
ENV HOME /
ENTRYPOINT ["/bin/crobat"]