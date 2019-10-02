-include .env

DEVOPS=../../infrastructure/devops
EXPLOREDATA=ansible-playbook $(DEVOPS)/exploredata.yml -i$(DEVOPS)/production.inventory -lexploredata

.PHONY: notebook hub up notebook-shell


notebook:
	docker build -t $(NOTEBOOK_IMAGE) build.notebook

hub:
	docker-compose build

up: hub notebook
	docker-compose up

pushtest:
	$(EXPLOREDATA) -eexploredata_src=$(PWD) -tpushtest

pushprod:
	$(EXPLOREDATA) -eexploredata_src=$(PWD) -tpushprod

notebook-shell: notebook
	docker run --rm -it --entrypoint=bash notebook
