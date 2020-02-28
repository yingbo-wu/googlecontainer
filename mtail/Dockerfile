FROM golang:1.12.3-alpine3.9

WORKDIR /go/src/github.com/google/mtail
RUN apk add --update --no-cache --virtual build-dependencies git make \
 && git clone https://github.com/google/mtail /go/src/github.com/google/mtail \
 && git checkout -b v3.0.0-rc34 \
 && make depclean \
 && make install_deps \
 && go build -o /usr/bin/mtail \
 && apk del build-dependencies

EXPOSE 3903

ENTRYPOINT ["/usr/bin/mtail"]
