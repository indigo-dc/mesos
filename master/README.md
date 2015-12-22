# mesos-master
Dockerfile to build Mesos Master docker image

<pre>
docker run -d \
-e MESOS_HOSTNAME=ip.address \
-e MESOS_IP=ip.address \
-e MESOS_QUORUM=2 \
-e MESOS_ZK=zk://node-1:2181,node-2:2181,node-3:2181/mesos \
--name mesos-master --net host --restart always mesos-master
</pre>
