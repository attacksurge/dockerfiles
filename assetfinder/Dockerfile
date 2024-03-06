FROM golang:alpine as build
RUN apk --no-cache add git
RUN go install github.com/tomnomnom/assetfinder@latest

FROM alpine:latest
COPY --from=build /go/bin/assetfinder /bin/assetfinder
ENV HOME /
ENTRYPOINT ["/bin/assetfinder"]
