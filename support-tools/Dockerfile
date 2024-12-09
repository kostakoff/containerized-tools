FROM docker.io/kostakoff/rocky-base-images:8-default
LABEL application=support-tools
USER root

COPY kubernetes.repo /etc/yum.repos.d/kubernetes.repo

RUN dnf -y install epel-release && \
  dnf -y install bash nmap netcat procps kubectl docker-ce-cli wget ncurses which

CMD sleep 1000
