docker_stack_name := etcd
service_replicas := 3

compose_files := -c docker-compose.yml

ifneq ("$(wildcard docker-compose.override.yml)","")
	compose_files += -c docker-compose.override.yml
endif

it: env
	@echo "make [deploy|destroy|network|plan]"

plan:
	docker stack config $(compose_files)

network:
	docker network create --scope=swarm --driver=overlay --attachable etcd-network

deploy:
	@env \
	ETCD_REPLICAS=$(service_replicas) \
	docker stack deploy $(compose_files) $(docker_stack_name)

destroy:
	docker stack rm $(docker_stack_name);
	docker network rm etcd--network

scale:
	docker service scale $(docker_stack_name)_etcd=$(service_replicas)
