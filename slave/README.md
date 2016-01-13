# mesos-slave

<pre>
docker run -d \
-e MESOS_HOSTNAME=$IP \
-e MESOS_IP=$IP \
-e MESOS_MASTER=zk://$IP-node1:2181,$IP-node2:2181,$IP-node3:2181/mesos \
-e MESOS_CONTAINERIZERS=docker,mesos \
-e MESOS_EXECUTOR_REGISTRATION_TIMEOUT=5mins \
-e MESOS_LOG_DIR=/var/log \
-e MESOS_docker_mesos_image=indigodatacloud/mesos-slave \
[-e MESOS_attributes="key1:value1;key2:value2;..."] \
-v /sys/fs/cgroup:/sys/fs/cgroup \
-v /var/run/docker.sock:/var/run/docker.sock \
--name slave --net host --privileged --pid host --restart always indigodatacloud/mesos-slave
</pre>

