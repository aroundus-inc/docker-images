REGISTRY=aroundus
IMAGE_NAME=sentry
SENTRY_VERSION=9.1.2
REVISION=2
VERSION=${SENTRY_VERSION}-${REVISION}

REGISTRY_TAG=${REGISTRY}/${IMAGE_NAME}

DOCKERFILE := Dockerfile
ifdef $$DOCKERFILE
	TMPDIR := $$DOCKERFILE
endif

image:
	docker build --rm -t ${REGISTRY_TAG}:${VERSION} --build-arg sentry_version=${SENTRY_VERSION} -f ${DOCKERFILE} --pull .
	docker tag ${REGISTRY_TAG}:${VERSION} ${REGISTRY_TAG}:latest

push: image
	docker push ${REGISTRY_TAG}:${VERSION}
	docker push ${REGISTRY_TAG}:latest
