Random internet user. Do not use this. It is my personal playground. :)

# Helpful Commands
docker run --rm -ti ubuntu:latest /bin/bash
docker ps

docker run --rm -p 8080:8081 -ti jboss/wildfly:8.2.0.Final /opt/jboss/wildfly/bin/standalone.sh -Djboss.http.port=8081 -Djboss.bind.address=0.0.0.0

docker run --rm -ti --cpuset-cpus="0,1" ubuntu:latest /bin/bash
docker run --rm -ti --cpuset-cpus="0" ubuntu:latest /bin/bash
nproc # to see the CPU effect

#Run Google's cAdvisor visualization tool
docker run --volume=/:/rootfs:ro --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8080:8080 --detach=true --name=cadvisor google/cadvisor:latest

#get a tree like ps view on coreos
ps axlfww

## Docker Forwarding

By setting the `$expose_docker_tcp` configuration value you can forward a local TCP port to docker on
each CoreOS machine that you launch. The first machine will be available on the port that you specify
and each additional machine will increment the port by 1.

Follow the [Enable Remote API instructions][coreos-enabling-port-forwarding] to get the CoreOS VM setup to work with port forwarding.

[coreos-enabling-port-forwarding]: https://coreos.com/docs/launching-containers/building/customizing-docker/#enable-the-remote-api-on-a-new-socket

Then you can then use the `docker` command from your local shell by setting `DOCKER_HOST`:

    export DOCKER_HOST=tcp://localhost:2375
