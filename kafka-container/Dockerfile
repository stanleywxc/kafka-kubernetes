FROM openjdk:8-jdk-alpine

RUN apk add --no-cache curl tar bash procps

ARG KAFKA_VERSION=2.5.0

RUN mkdir -p /opt && \
    cd /opt && \
    curl -k https://mirrors.koehn.com/apache/kafka/${KAFKA_VERSION}/kafka_2.12-${KAFKA_VERSION}.tgz | \
        tar -zx && \
    ln -s kafka_2.12-${KAFKA_VERSION} kafka && \
    echo kafka ${KAFKA_VERSION} installed in /opt


ENV KAFKA_HOME=/opt/kafka
ENV PATH=$PATH:$KAFKA_HOME/bin

ADD start-zookeeper start-broker /
ADD zookeeper.kubernetes.properties /opt/kafka/config/zookeeper.kubernetes.properties
ADD server.kubernetes.properties /opt/kafka/config/server.kubernetes.properties
ADD producer.properties /opt/kafka/config/producer.properties
ADD consumer.properties /opt/kafka/config/consumer.properties

