FROM golang:alpine as build
RUN apk --no-cache add git
RUN GO111MODULE=on go install github.com/d3mondev/puredns/v2@latest
RUN apk --no-cache --virtual .build-deps add git build-base \
   && git clone --depth=1 https://github.com/blechschmidt/massdns.git \
   && cd massdns && make && apk del .build-deps
#WORKDIR /massdns/

FROM alpine:latest
ENV HOME /
COPY --from=build /go/bin/puredns /bin/puredns
COPY --from=build /go/massdns/bin/massdns /bin/massdns
ENTRYPOINT ["/bin/puredns"]
