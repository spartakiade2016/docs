# How to setup [Consul](https://consul.io/)

Consul makes it simple for services to register themselves and to discover
other services via a DNS or HTTP interface. Register external services such
as SaaS providers as well.

Pairing service discovery with health checking prevents routing requests to
unhealthy hosts and enables services to easily provide circuit breakers.

## Setup

~~~ sh
# on node-1
docker run -d \
  --name=consul \
  --restart=always \
  --net=host \
  --privileged \
  -e SERVICE_IGNORE=true \
  unfall24/consul-server:0.6 -advertise ???.???.???.001 -bootstrap-expect 3

# on node-2
docker run -d \
  --name=consul \
  --restart=always \
  --net=host \
  --privileged \
  -e SERVICE_IGNORE=true \
  unfall24/consul-server:0.6 -advertise ???.???.???.002 -join ???.???.???.001

# on node-3
docker run -d \
  --name=consul \
  --restart=always \
  --net=host \
  --privileged \
  -e SERVICE_IGNORE=true \
  unfall24/consul-server:0.6 -advertise ???.???.???.002 -join ???.???.???.001
~~~

You should now be able to access the Consul UI using one of the following URLs:

* [http://???.???.???.001:8500/ui/](http://???.???.???.001:8500/ui/)
* [http://???.???.???.002:8500/ui/](http://???.???.???.002:8500/ui/)
* [http://???.???.???.002:8500/ui/](http://???.???.???.002:8500/ui/)
