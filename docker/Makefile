REGISTRY?=qsslcaudit
VERSION=0.1
DOCKERFILES=$(shell find * -type f -name Dockerfile)
IMAGES=$(subst /,\-,$(subst /Dockerfile,,$(DOCKERFILES)))


.PHONY: all

all: $(IMAGES)

debug: 
	echo $(IMAGES)

%:
	docker build -t $(REGISTRY)/$@:$(VERSION) -f $(subst -,/,$@)/Dockerfile ../ > $@_build.log
	# -docker build -t $(REGISTRY)/$@ -f $(subst -,/,$@)/Dockerfile ../ 2>&1 | \
	# tee $@.log | sed -e 's/^/$@: /'
