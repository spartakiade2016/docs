# How to setup [Registrator](http://gliderlabs.com/registrator/latest/)

Registrator automatically registers and deregisters services for any Docker container
by inspecting containers as they come online. Registrator supports pluggable service
registries, which currently includes [Consul](http://www.consul.io/),
[etcd](https://github.com/coreos/etcd) and [SkyDNS 2](https://github.com/skynetservices/skydns/).

## Setup

~~~ sh
# on node-1
docker run -d -h $HOSTNAME \
    --name=registrator \
    --restart=always \
    --volume=/var/run/docker.sock:/tmp/docker.sock \
    gliderlabs/registrator:latest -ip ???.???.???.001 consul://???.???.???.001:8500

# on node-2
docker run -d -h $HOSTNAME \
    --name=registrator \
    --restart=always \
    --volume=/var/run/docker.sock:/tmp/docker.sock \
    gliderlabs/registrator:latest -ip ???.???.???.002 consul://???.???.???.002:8500

# on node-3
docker run -d -h $HOSTNAME \
    --name=registrator \
    --restart=always \
    --volume=/var/run/docker.sock:/tmp/docker.sock \
    gliderlabs/registrator:latest -ip ???.???.???.003 consul://???.???.???.003:8500
~~~
