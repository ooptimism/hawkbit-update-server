FROM qingfeng1987/hawkbit-update-server:0.3.0M7

ENV MARIADB_DRIVER_VERSION=2.7.2


RUN set -x \
    && apk add --no-cache --virtual build-dependencies gnupg unzip libressl wget \
    && wget -O $JAVA_HOME/lib/ext/mariadb-java-client.jar --no-verbose https://downloads.mariadb.com/Connectors/java/connector-java-$MARIADB_DRIVER_VERSION/mariadb-java-client-$MARIADB_DRIVER_VERSION.jar \
    && wget -O $JAVA_HOME/lib/ext/mariadb-java-client.jar.asc --no-verbose https://downloads.mariadb.com/Connectors/java/connector-java-$MARIADB_DRIVER_VERSION/mariadb-java-client-$MARIADB_DRIVER_VERSION.jar.asc \
    && apk del build-dependencies

VOLUME "$HAWKBIT_HOME"

ENTRYPOINT ["java","-jar","/opt/hawkbit-update-server.jar","--spring.profiles.active=mysql","-Xms768m -Xmx768m -XX:MaxMetaspaceSize=250m -XX:MetaspaceSize=250m -Xss300K -XX:+UseG1GC -XX:+UseStringDeduplication -XX:+UseCompressedOops -XX:+HeapDumpOnOutOfMemoryError"]
