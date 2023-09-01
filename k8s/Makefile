.DEFAULT_GOAL := help
file := $2
IN_DIR = $(PWD)

.PHONY: help
help: ## Print the help message
	 @awk 'BEGIN {FS = ":.*?## "} /^[0-9a-zA-Z_-]+:.*?## / {printf "\033[36m%s\033[0m : %s\n", $$1, $$2}' $(MAKEFILE_LIST) | \
                sort | \
                column -s ':' -t

.PHONY: create
create: ## Create the iris app
	kubectl apply -k admin; \
	kubectl apply -k mysql; \
	kubectl apply -k espocrm-ui; \
	kubectl apply -k espocrm-daemon; \
	kubectl apply -k espocrm-websocket;

.PHONY: delete
delete:
	kubectl delete -k admin; \
	kubectl delete -k mysql; \
	kubectl delete -k espocrm-ui; \
	kubectl delete -k espocrm-daemon; \
	kubectl delete -k espocrm-websocket;

.PHONY: deploy-specific-kustomization
deploy-specific-kustomization: ## Delpoy specific kustomization (ex- make deploy-specific-kustomization ARGS="path of kustomization.yml dir")
	kubectl apply -k $(ARGS)

.PHONY: delete-specific-kustomization
delete-specific-kustomization: ## Delete specific kustomization (ex- make delete-specific-kustomization ARGS="path of kustomization.yml dir")
	kubectl delete -k $(ARGS)

.PHONY: deploy-specific-manifest
deploy-specific-manifest: ## deploy specific manifest (ex- make deploy-specific-manifest ARGS="path of manifest dir")
	kubectl apply -f $(ARGS)

.PHONY: delete-specific-manifest
delete-specific-manifest: ## delete specific manifest (ex- make delete-specific-manifest ARGS="path of manifest dir")
	kubectl apply -f $(ARGS)