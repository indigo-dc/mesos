FROM dodasts/mesos-base:ubuntu

RUN apt-get update \
    && apt-get install -y --no-install-recommends apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common \
    && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - \
    && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" \
    && apt-get update \
    && apt-get install -y --no-install-recommends docker-ce \
    && apt-get autoremove \
    && apt-get clean

ENV MESOS_WORK_DIR /tmp/mesos
ENV MESOS_CONTAINERIZERS docker,mesos

# https://mesosphere.github.io/marathon/docs/native-docker.html
ENV MESOS_EXECUTOR_REGISTRATION_TIMEOUT 5mins

VOLUME /tmp/mesos

COPY entrypoint.sh /usr/sbin/

ENTRYPOINT ["/usr/sbin/entrypoint.sh"]
CMD ["/usr/sbin/mesos-slave"]
