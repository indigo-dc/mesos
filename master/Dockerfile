FROM ubuntu:16.04

ARG mesos_version

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF && \
echo deb http://repos.mesosphere.com/ubuntu xenial main > /etc/apt/sources.list.d/mesosphere.list && \
apt-get update && \
apt-get -y install --no-install-recommends openjdk-8-jre-headless mesos=${mesos_version} && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["/usr/sbin/mesos-master"]

ENV MESOS_WORK_DIR /tmp/mesos

VOLUME /tmp/mesos

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
