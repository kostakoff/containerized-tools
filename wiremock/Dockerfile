FROM docker.io/kostakoff/rocky-base-images:8-openjdk11
LABEL application=wiremock
#USER root

# Add Wiremock
ENV WIREMOCK_VERSION 3.5.2
ADD --chown=appuser:appuser https://repo.maven.apache.org/maven2/org/wiremock/wiremock-standalone/${WIREMOCK_VERSION}/wiremock-standalone-${WIREMOCK_VERSION}.jar /app/wiremock-standalone.jar
ENV WIREMOCK_OPTIONS='--port 8080 --bind-address 0.0.0.0 --root-dir /app/wiremock --enable-stub-cors --async-response-enabled --async-response-threads 15 --local-response-templating --global-response-templating'
RUN mkdir -p /app/wiremock

USER appuser
CMD java $JAVA_OPTS -jar wiremock-standalone.jar $WIREMOCK_OPTIONS
