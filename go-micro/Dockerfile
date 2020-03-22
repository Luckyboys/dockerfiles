FROM golang:1.13 as builder

RUN go env -w GO111MODULE="on"
RUN go env -w GOPROXY="https://goproxy.cn,direct"

RUN go get github.com/micro/micro/v2

FROM centos:7

ENV MICRO_REGISTRY etcd
ENV MICRO_REGISTRY_ADDRESS 127.0.0.1:2379

COPY --from=builder /go/bin/micro /bin/micro
