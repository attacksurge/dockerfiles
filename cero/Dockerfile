FROM golang:alpine as build
RUN apk --no-cache add git
RUN git clone https://github.com/glebarez/cero.git
RUN cd cero; go install

FROM alpine:latest
COPY --from=build /go/bin/cero /bin/cero
ENV HOME /
ENTRYPOINT ["/bin/cero"]
