#include env_make
NS = dvin
VERSION ?= 1.0.1

REPO = gvmd
#NAME = name of the image
#INSTANCE = default

#.PHONY: build push shell run start stop rm release

build:
	docker build -t $(NS)/$(REPO):$(VERSION) .

push:
	docker push $(NS)/$(REPO):$(VERSION)
