FROM golang:alpine

RUN apk add --no-cache git &&\
  go get github.com/ChronixDB/chronix.ingester &&\
  apk del git

EXPOSE 8080
CMD [ "/go/bin/chronix.ingester" "-chronix-url=http://chronix:8983/solr/chronix"]
