FROM dodasts/mesos-base:ubuntu

ENV MESOS_WORK_DIR /tmp/mesos

VOLUME /tmp/mesos

COPY entrypoint.sh /usr/sbin/

ENTRYPOINT ["/usr/sbin/entrypoint.sh"]
CMD ["/usr/sbin/mesos-master"]
