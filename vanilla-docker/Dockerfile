FROM ubuntu:14.04.4

MAINTAINER Christian Oelsner <c.oelsner@web.de>

RUN apt-get update && apt-get install -y zip wget && apt-get clean 

ENV VERSION=1353 ZIP=terraria-server.zip

WORKDIR /opt/terraria

# uncomment for local debugging
# ADD ./terraria-server-${VERSION}.zip ${ZIP}

ADD http://terraria.org/server/terraria-server-${VERSION}.zip ${ZIP}

RUN unzip $ZIP 'Linux/*' && rm $ZIP \
  && chmod -R a+rw ./Linux/* \
  && chmod a+x ./Linux/TerrariaServer*

VOLUME ["/world"]
EXPOSE 7777

ADD serverconfig.txt ./Linux/

ENTRYPOINT ["./Linux/TerrariaServer", "-x64", "-config", "Linux/serverconfig.txt"]

