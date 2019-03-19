FROM store/oracle/serverjre:8

ENV KAFKA_HOME=/app/kafka \
    KAFKA_VERSION=2.1.1

RUN mkdir -p ${KAFKA_HOME} \
    && curl https://www.apache.org/dist/kafka/${KAFKA_VERSION}/kafka_2.12-${KAFKA_VERSION}.tgz -o ${KAFKA_HOME}/kafka_2.12-${KAFKA_VERSION}.tgz \
    && curl https://www.apache.org/dist/kafka/${KAFKA_VERSION}/kafka_2.12-${KAFKA_VERSION}.tgz.asc -o ${KAFKA_HOME}/kafka_2.12-${KAFKA_VERSION}.tgz.asc \
    && curl https://www.apache.org/dist/kafka/KEYS -o ${KAFKA_HOME}/KEYS

WORKDIR ${KAFKA_HOME}

RUN gpg --import KEYS \
    && gpg --verify kafka_2.12-${KAFKA_VERSION}.tgz.asc kafka_2.12-${KAFKA_VERSION}.tgz \
    && tar -xvf kafka_2.12-${KAFKA_VERSION}.tgz --strip-components 1 \
    && rm -Rf kafka_2.12-${KAFKA_VERSION}.tgz.asc \
    && rm -Rf kafka_2.12-${KAFKA_VERSION}.tgz \
    && rm -Rf KEYS

COPY config/server.properties ${KAFKA_HOME}/config/server.properties

EXPOSE 9093