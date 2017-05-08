FROM openjdk:8-jre-alpine

RUN apk add --no-cache bash curl &&\
  cd / &&\
  curl -LO https://github.com/ChronixDB/chronix.server/releases/download/v0.5-beta/chronix-0.5-beta.zip &&\
  echo '5c7f022b6a7028e31e958f36d64fa960092ad93394002011fb02083c64d823c2  /chronix-0.5-beta.zip' | sha256sum -c - &&\
  unzip chronix-0.5-beta.zip &&\
  rm chronix-0.5-beta.zip &&\
  cd chronix-solr-6.4.2 &&\
  chmod +x bin/solr &&\
  adduser -Du 1000 chronix &&\
  chown -R chronix /chronix-solr-6.4.2 &&\
  mv /chronix-solr-6.4.2/server/solr/chronix/data /data &&\
  mv /chronix-solr-6.4.2/server/solr/chronix/conf /conf &&\
  ln -s /data /chronix-solr-6.4.2/server/solr/chronix/data &&\
  ln -s /conf /chronix-solr-6.4.2/server/solr/chronix/conf &&\
  apk del curl

USER chronix
WORKDIR /chronix-solr-6.4.2
EXPOSE 8983
VOLUME /data /conf
CMD ["./bin/solr", "start", "-f" ] 
