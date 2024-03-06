FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install github.com/tomnomnom/anew@latest

FROM alpine:latest
COPY --from=build /go/bin/anew /bin/anew
ENV HOME /
ENTRYPOINT ["/bin/anew"]
