FROM ubuntu:16.04

ARG mesos_version

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF && \
echo deb http://repos.mesosphere.com/ubuntu xenial main > /etc/apt/sources.list.d/mesosphere.list && \
apt-get update && \
apt-get -y install --no-install-recommends curl apt-transport-https openjdk-8-jre-headless mesos=${mesos_version} && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - && \
echo "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable" > /etc/apt/sources.list.d/docker.list && \
apt-get update && \
apt-get install -y docker-ce docker-ce-cli containerd.io && \
apt-get clean && rm -rf /var/lib/apt/lists/*

CMD ["/usr/sbin/mesos-slave"]

ENV MESOS_WORK_DIR /tmp/mesos
ENV MESOS_CONTAINERIZERS docker,mesos
ENV MESOS_SYSTEMD_ENABLE_SUPPORT false

# https://mesosphere.github.io/marathon/docs/native-docker.html
ENV MESOS_EXECUTOR_REGISTRATION_TIMEOUT 5mins

VOLUME /tmp/mesos

COPY entrypoint.sh /
RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]




