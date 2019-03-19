FROM store/oracle/serverjre:8

ENV ZOOKEEPER_HOME=/app/zookeeper \
    ZOOKEEPER_VERSION=3.4.13

RUN mkdir -p ${ZOOKEEPER_HOME} \
    && curl https://www.apache.org/dist/zookeeper/stable/zookeeper-${ZOOKEEPER_VERSION}.tar.gz -o ${ZOOKEEPER_HOME}/zookeeper-${ZOOKEEPER_VERSION}.tar.gz \
    && curl https://www.apache.org/dist/zookeeper/stable/zookeeper-${ZOOKEEPER_VERSION}.tar.gz.sha1 -o ${ZOOKEEPER_HOME}/zookeeper-${ZOOKEEPER_VERSION}.tar.gz.sha1

WORKDIR ${ZOOKEEPER_HOME}

RUN sha1sum -c zookeeper-${ZOOKEEPER_VERSION}.tar.gz.sha1 \
    && tar -xvf zookeeper-${ZOOKEEPER_VERSION}.tar.gz --strip-components 1 \
    && rm -Rf zookeeper-${ZOOKEEPER_VERSION}.tar.gz.sha1 \
    && rm -Rf zookeeper-${ZOOKEEPER_VERSION}.tar.gz 

COPY config/zoo.cfg ${ZOOKEEPER_HOME}/conf/zoo.cfg

EXPOSE 2181:2181