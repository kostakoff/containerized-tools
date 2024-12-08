FROM docker.io/kostakoff/rocky-base-images:8-default
LABEL application=ssh-server
USER root

RUN usermod -s /bin/bash appuser && \
    echo 'appuser:appuser' | chpasswd

COPY id_rsa.pub.example /home/appuser/.ssh/authorized_keys
RUN chown -R appuser:appuser /home/appuser/.ssh && \
    chmod 600 /home/appuser/.ssh/authorized_keys

COPY test.sh /home/appuser/test.sh
RUN chmod +x /home/appuser/test.sh

RUN dnf install -y openssh-server procps && \
    echo 'Port 2222' >> /etc/ssh/sshd_config && \
    echo 'PidFile /tmp/sshd.pid' >> /etc/ssh/sshd_config && \
    ssh-keygen -A && \
    chown appuser:appuser -R /etc/ssh && \
    rm /run/nologin

USER appuser
WORKDIR /home/appuser

CMD exec /usr/sbin/sshd -D -e
EXPOSE 2222
