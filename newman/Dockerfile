FROM docker.io/kostakoff/rocky-base-images:8-nodejs20
LABEL application=newman
USER root

COPY --chown=appuser:appuser google.com.json /app/google.com.json
RUN npm install -g newman

USER appuser
RUN newman run google.com.json

CMD newman run /app/collection.json
