REGISTRY_NAME?=docker.io/hashicorp
VERSION=1.5.5
IMAGE_TAG_ENT=$(REGISTRY_NAME)/vault-enterprise:$(VERSION)-ubi-ent
IMAGE_TAG_OSS=$(REGISTRY_NAME)/vault:$(VERSION)-ubi

.PHONY: build ent-image oss-image

build: ent-image oss-image

ent-image:
	docker build --build-arg VAULT_VERSION=$(VERSION)+ent --no-cache -t $(IMAGE_TAG_ENT) .
	docker tag $(IMAGE_TAG_ENT) $(REGISTRY_NAME)/vault-enterprise:latest

oss-image:
	docker build --build-arg VAULT_VERSION=$(VERSION) --no-cache -t $(IMAGE_TAG_OSS) .
	docker tag $(IMAGE_TAG_OSS) $(REGISTRY_NAME)/vault:latest
