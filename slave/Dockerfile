FROM dodasts/mesos-base:ubuntu

RUN apt-get update \
    && apt-get install -y --no-install-recommends wget \
    && apt-get autoremove \
    && apt-get clean \
    && wget https://packages.docker.com/1.12/apt/repo/pool/main/d/docker-engine/docker-engine_1.12.6~cs8-0~ubuntu-xenial_amd64.deb -o /tmp/docker-engine.deb \
    && dpkg -i /tmp/docker-engine.deb \
    && rm /tmp/docker-engine.deb

ENV MESOS_WORK_DIR /tmp/mesos
ENV MESOS_CONTAINERIZERS docker,mesos

# https://mesosphere.github.io/marathon/docs/native-docker.html
ENV MESOS_EXECUTOR_REGISTRATION_TIMEOUT 5mins

VOLUME /tmp/mesos

COPY entrypoint.sh /usr/sbin/

ENTRYPOINT ["/usr/sbin/entrypoint.sh"]
CMD ["/usr/sbin/mesos-slave"]
