我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

<a href="https://rpcx.site/"><img height="160" src="http://rpcx.site/logos/rpcx-logo-text.png"></a>

Official site: [http://rpcx.site](http://rpcx.site/)

[![License](https://img.shields.io/:license-apache%202-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![GoDoc](https://godoc.org/github.com/smallnest/rpcx?status.png)](http://godoc.org/github.com/smallnest/rpcx)  [![travis](https://travis-ci.org/smallnest/rpcx.svg?branch=master)](https://travis-ci.org/smallnest/rpcx) [![Go Report Card](https://goreportcard.com/badge/github.com/smallnest/rpcx)](https://goreportcard.com/report/github.com/smallnest/rpcx) [![coveralls](https://coveralls.io/repos/smallnest/rpcx/badge.svg?branch=master&service=github)](https://coveralls.io/github/smallnest/rpcx?branch=master) [![QQ群](https://img.shields.io/:QQ群-398044387-blue.svg)](_documents/images/rpcx_qq.png) [![sourcegraph](https://sourcegraph.com/github.com/smallnest/rpcx/-/badge.svg)](https://sourcegraph.com/github.com/smallnest/rpcx?badge)


**Notice: You can write clients in any programming languages to call rpcx services via [rpcx-gateway](https://github.com/rpcx-ecosystem/rpcx-gateway)**


> If you can write Go methods, you can also write rpc services. It is so easy to write rpc applications with rpcx.

## Installation

install the basic features:

`go get -u -v github.com/smallnest/rpcx/...`


If you want to use `reuseport`、`quic`、`kcp`, `zookeeper`, `etcd`, `consul` registry, use those tags to `go get` 、 `go build` or `go run`. For example, if you want to use all features, you can:

```sh
go get -u -v -tags "reuseport quic kcp zookeeper etcd consul ping" github.com/smallnest/rpcx/...
```

**_tags_**:
- **quic**: support quic transport
- **kcp**: support kcp transport
- **zookeeper**: support zookeeper register
- **etcd**: support etcd register
- **consul**: support consul register
- **ping**: support network quality load balancing
- **reuseport**: support reuseport

## Features
rpcx is a RPC framework like [Alibaba Dubbo](http://dubbo.io/) and [Weibo Motan](https://github.com/weibocom/motan).

**rpcx 3.0** has been refactored for targets:
1. **Simple**: easy to learn, easy to develop, easy to intergate and easy to deploy
2. **Performance**: high perforamnce (>= grpc-go)
3. **Cross-platform**: support _raw slice of bytes_, _JSON_, _Protobuf_ and _MessagePack_. Theoretically it can be use in java, php, python, c/c++, node.js, c# and other platforms
4. **Service discovery and service governance.**: support zookeeper, etcd and consul.


It contains below features
- Support raw Go functions,. No need to define proto files.
- Pluggable. Features can be extended such as service discovery, tracing.
- Support TCP, HTTP, [QUIC](https://en.wikipedia.org/wiki/QUIC) and [KCP](https://github.com/skywind3000/kcp)
- Support multiple codecs such as JSON、[Protobuf](https://github.com/skywind3000/kcp)、[MessagePack](https://msgpack.org/index.html) and raw bytes.
- Service discovery. Support peer2peer, configured peers, [zookeeper](https://zookeeper.apache.org), [etcd](https://github.com/coreos/etcd), [consul](https://www.consul.io) and [mDNS](https://en.wikipedia.org/wiki/Multicast_DNS).
- Fault tolerance：Failover、Failfast、Failtry.
- Load banlancing：support Random, RoundRobin, Consistent hashing, Weighted, network quality and Geography.
- Support Compression.
- Support passing metadata.
- Support Authorization.
- Support heartbeat and one-way request.
- Other features: metrics, log, timeout, alias, CircuitBreaker.
- Support bidirectional communication.
- Support access via HTTP so you can write clients in any programming languages
- Support API gateway.
- Support backup request, forking and broadcast.


rpcx uses a binary protocol and platform-independent, that means you can develop services in other languages such as Java, python, nodejs, and you can use other prorgramming languages to invoke services developed in Go.

There is a UI manager: [rpcx-ui](https://github.com/smallnest/rpcx-ui).

## Performance

**_Test Environment_**

- **CPU**: Intel(R) Xeon(R) CPU E5-2630 v3 @ 2.40GHz, 32 cores
- **Memory**: 32G
- **Go**: 1.9.0
- **OS**: CentOS 7 / 3.10.0-229.el7.x86_64

**_Use_**
- protobuf
- the client and the server on the same server
- 581 bytes payload
- 500/2000/5000 concurrent clients
- mock processing time: 0ms, 10ms and 30ms

**_Test Result_**

### 0ms process time

<table><tr><th>Throughputs</th><th>Mean Latency</th><th>P99 Latency</th></tr><tr><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p0-throughput.png"></td><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p0-latency.png"></td><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p0-p99.png"></td></tr></table>


### 10ms process time

<table><tr><th>Throughputs</th><th>Mean Latency</th><th>P99 Latency</th></tr><tr><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p10-throughput.png"></td><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p10-latency.png"></td><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p10-p99.png"></td></tr></table>


### 30ms process time

<table><tr><th>Throughputs</th><th>Mean Latency</th><th>P99 Latency</th></tr><tr><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p30-throughput.png"></td><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p30-latency.png"></td><td width="30%"><img src="http://colobu.com/2018/01/31/benchmark-2018-spring-of-popular-rpc-frameworks/p30-p99.png"></td></tr></table>


## Examples

You can find all examples at [rpcx-ecosystem/rpcx-examples3](https://github.com/rpcx-ecosystem/rpcx-examples3).

The below is a simple example.


**Server**

```go
    // define example.Arith
    ……

    s := server.NewServer()
	s.RegisterName("Arith", new(example.Arith), "")
	s.Serve("tcp", addr)

```


**Client**

```go
    // prepare requests
    ……

    d := client.NewPeer2PeerDiscovery("tcp@"+addr, "")
	xclient := client.NewXClient("Arith", client.Failtry, client.RandomSelect, d, client.DefaultOption)
	defer xclient.Close()
	err := xclient.Call(context.Background(), "Mul", args, reply, nil)
```

## Productions

- Cluster defense project： 4 billion of calls per day (2 server, 8 clients)
- [Storm of the Three Kingdoms](https://www.juxia.com/sjwy/game-2747.html): game
- 车弹趣
- 撩车友
- 迈布

If you or your company is using rpcx, welcome to tell me and I will add more in this.

## Contribute

see [contributors](https://github.com/smallnest/rpcx/graphs/contributors).

Welcome to contribute:
- submit issues or requirements
- send PRs
- write projects to use rpcx
- write tutorials or articles to introduce rpcx

## License

Apache License, Version 2.0 
