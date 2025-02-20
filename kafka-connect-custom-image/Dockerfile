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
RUN wget https://repo1.maven.org/maven2/org/mongodb/kafka/mongo-kafka-connect/1.15.0/mongo-kafka-connect-1.15.0-all.jar -O /tmp/mongo-kafka-connect-1.15.0-all.jar
RUN wget https://repo1.maven.org/maven2/org/apache/avro/avro/1.12.0/avro-1.12.0.jar -O /tmp/avro-1.12.0.jar
RUN wget https://repo1.maven.org/maven2/org/mongodb/mongodb-driver-sync/5.3.1/mongodb-driver-sync-5.3.1.jar -O /tmp/mongodb-driver-sync-5.3.1.jar
FROM quay.io/strimzi/kafka:0.45.0-kafka-3.9.0 AS final
USER root:root
RUN mkdir -p /opt/kafka/plugins/debezium
COPY --from=downloader /tmp /opt/kafka/plugins/debezium/
USER 1001