FROM store/oracle/serverjre:8

ENV IGNITE_HOME=/app/ignite \
    IGNITE_VERSION=2.7.0

RUN mkdir -p ${IGNITE_HOME} \
    && curl https://www.apache.org/dist/ignite/${IGNITE_VERSION}/apache-ignite-${IGNITE_VERSION}-bin.zip -o ${IGNITE_HOME}/apache-ignite-${IGNITE_VERSION}-bin.zip \
    && curl https://www.apache.org/dist/ignite/${IGNITE_VERSION}/apache-ignite-${IGNITE_VERSION}-bin.zip.sha512 -o ${IGNITE_HOME}/apache-ignite-${IGNITE_VERSION}-bin.zip.sha512 

WORKDIR ${IGNITE_HOME}

RUN yum -q -y update \
    && yum -q -y install unzip \
    && sha512sum -c apache-ignite-${IGNITE_VERSION}-bin.zip.sha512  \
    && unzip apache-ignite-${IGNITE_VERSION}-bin.zip \
    && rm -Rf apache-ignite-${IGNITE_VERSION}-bin.zip \
    && rm -Rf apache-ignite-${IGNITE_VERSION}-bin.zip.sha512 \
    && mv apache-ignite-${IGNITE_VERSION}-bin/* . \
    && rm -Rf apache-ignite-${IGNITE_VERSION}-bin \
    && mv libs/optional/ignite-rest-http libs/ignite-rest-http \
    && mv libs/optional/ignite-kubernetes libs/ignite-kubernetes

EXPOSE 11211 47100 47500 49112 8080