FROM ubuntu:14.04

#RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF && \
#echo deb http://repos.mesosphere.io/ubuntu trusty main > /etc/apt/sources.list.d/mesosphere.list && \
#apt-get update && \
#apt-get -y install --no-install-recommends mesos && \
#rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN apt-get update && \
apt-get install -y --no-install-recommends curl gdebi-core openjdk-7-jre-headless && \
curl https://raw.githubusercontent.com/indigo-dc/mesos/devel/dist/0.28/mesos-0.28.0-0.1.deb -o mesos-0.28.0-0.1.deb && \
gdebi --n mesos-0.28.0-0.1.deb && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#CMD ["/usr/sbin/mesos-master"]
CMD ["/usr/local/sbin/mesos-master"]

ENV MESOS_WORK_DIR /tmp/mesos

VOLUME /tmp/mesos

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
