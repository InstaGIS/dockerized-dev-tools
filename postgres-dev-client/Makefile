SHELL = /usr/bin/env bash

docker_image_name = jtrhinstagis/postgres-dev-client

.PHONY: build-docker-image push-docker-image

build-docker-image:
	docker build -t $(docker_image_name) .

push-docker-image: build-docker-image
	docker push $(docker_image_name)
