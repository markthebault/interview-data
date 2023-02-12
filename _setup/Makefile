IMAGE_NAME=markthebault/vscode-interview:latest

build.m1:
	docker buildx build --platform linux/amd64 -t $(IMAGE_NAME) --push .

deploy:
	kubectl create ns interview-test || true
	kubectl apply -f k8s-code-server.yaml

destroy:
	kubectl delete -f k8s-code-server.yaml
	kubectl delete ns interview-test || true