FROM ubuntu:20.04

ENV DAITAKU_HOME=/opt/daitaku
ENV DAITAKU_PORT=11000
ENV DAITAKU_VERSION=9.0.1

RUN apt-get update && apt-get upgrade -y && apt-get install curl -y && \
    mkdir /usr/local/daitaku && \
    curl -Lf https://cdn.downloads.dataiku.com/public/dss/$DAITAKU_VERSION/dataiku-dss-$DAITAKU_VERSION.tar.gz -o /tmp/daitaku.tar.gz && \
    tar xzf /tmp/daitaku.tar.gz -C /usr/local/daitaku --strip-components=1 && \
    mkdir $DAITAKU_HOME && \
    adduser --disabled-password --gecos "" daitaku && \
    chown -R daitaku: $DAITAKU_HOME /usr/local/daitaku && \
    /usr/local/daitaku/scripts/install/install-deps.sh -yes && \
    su - daitaku -c "/usr/local/daitaku/installer.sh -d $DAITAKU_HOME -p $DAITAKU_PORT" && \
    rm -rf /tmp/daitaku.tar.gz

USER daitaku

WORKDIR $DAITAKU_HOME

EXPOSE ${DAITAKU_PORT}

CMD ["bin/dss","run"]