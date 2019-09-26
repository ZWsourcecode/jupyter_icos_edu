-include .env

.PHONY: notebook hub up notebook-shell


notebook:
	docker build -t $(NOTEBOOK_IMAGE) build.notebook

hub:
	docker-compose build

up: hub notebook
	docker-compose up

pushtest:
	../../infrastructure/devops/deploy.py exploredata pushtest -eexploredata_src=$(PWD)

notebook-shell: notebook
	docker run --rm -it --entrypoint=bash notebook
