build:
	protoc -I. --go_out=plugins=micro:$(GOPATH)/src/shippy/consignment-cli \
		proto/consignment/consignment.proto
	docker build -t consignment-cli .

run:
	docker run -e MICRO_REGISTRY=mdns consignment-cli
