FROM alpine AS downloader
RUN apk add --no-cache wget tar
RUN wget https://repo1.maven.org/maven2/io/debezium/debezium-connector-postgres/3.0.7.Final/debezium-connector-postgres-3.0.7.Final-plugin.tar.gz && \
    tar -C /tmp -xvf debezium-connector-postgres-3.0.7.Final-plugin.tar.gz
RUN wget https://repo1.maven.org/maven2/io/debezium/debezium-connector-mongodb/3.0.7.Final/debezium-connector-mongodb-3.0.7.Final-plugin.tar.gz && \
    tar -C /tmp -xvf debezium-connector-mongodb-3.0.7.Final-plugin.tar.gz
RUN wget https://repo1.maven.org/maven2/io/debezium/debezium-connector-jdbc/3.0.7.Final/debezium-connector-jdbc-3.0.7.Final-plugin.tar.gz && \
    tar -C /tmp -xvf debezium-connector-jdbc-3.0.7.Final-plugin.tar.gz
RUN wget https://repo1.maven.org/maven2/io/debezium/debezium-connector-mysql/3.0.7.Final/debezium-connector-mysql-3.0.7.Final-plugin.tar.gz && \
    tar -C /tmp -xvf debezium-connector-mysql-3.0.7.Final-plugin.tar.gz

FROM quay.io/strimzi/kafka:0.45.0-kafka-3.9.0 AS final
USER root:root
RUN mkdir -p /opt/kafka/plugins/debezium
COPY --from=downloader /tmp /opt/kafka/plugins/debezium/
USER 1001