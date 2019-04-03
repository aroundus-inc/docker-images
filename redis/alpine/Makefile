REGISTRY=aroundus
IMAGE_NAME=redis-kubectl
REDIS_VERSION=4.0.14
REVISION=1
VERSION=${REDIS_VERSION}-${REVISION}-alpine

REGISTRY_TAG=${REGISTRY}/${IMAGE_NAME}

DOCKERFILE := Dockerfile
ifdef $$DOCKERFILE
	TMPDIR := $$DOCKERFILE
endif

image:
	docker build --rm -t ${REGISTRY_TAG}:${VERSION} --build-arg redis_version=${REDIS_VERSION}-alpine -f ${DOCKERFILE} --pull .
	docker tag ${REGISTRY_TAG}:${VERSION} ${REGISTRY_TAG}:alpine

push: image
	docker push ${REGISTRY_TAG}:alpine
	docker push ${REGISTRY_TAG}:${VERSION}
