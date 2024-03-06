# Docker Swarm Stack compose file for `etcd`

Simple `Makefile` and compose for deploying an `etcd` cluster to a
Docker Swarm environment. It assumes there are 3 Swarm managers, and
that the manager nodes have a `etcd` Label assigned to them.

You can create the node labels with:

```
docker node update --label-add etcd_node=true <node-1>
docker node update --label-add etcd_node=true <node-2>
docker node update --label-add etcd_node=true <node-3>

```

To remove the node labels:

```
docker node update --label-rm etcd_node <node-1>
docker node update --label-rm etcd_node <node-2>
docker node update --label-rm etcd_node <node-3>
```

# To deploy the `etcd` stack and create the Overlay network

```
make network
make deploy
```

# To remove the `etcd` stack and Overlay network

```
make destroy
```
