# Not-Uber App - Rides on Demand

This is a demo application that consists of several microservices and illustrates
the use of the OpenTracing API. It can be run standalone, but requires Jaeger backend
to view the traces. This tutorial / walkthough is  a modified version of the below blog:
  * as a blog post [Take OpenTracing for a HotROD ride][hotrod-tutorial]

## Features

* Discover architecture of the whole system via data-driven dependency diagram
* View request timeline & errors, understand how the app works
* Find sources of latency, lack of concurrency
* Highly contextualized logging
* Use baggage propagation to
  * Diagnose inter-request contention (queueing)
  * Attribute time spent in a service
* Use open source libraries with OpenTracing integration to get vendor-neutral instrumentation for free

## Running

### Run Jaeger Backend

An all-in-one Jaeger backend is packaged as a Docker container with in-memory storage.

```
docker run -d -p6831:6831/udp -p16686:16686 jaegertracing/all-in-one:latest
```

Jaeger UI can be accessed at http://localhost:16686.

### Run Not-Uber Application

```
go get github.com/jaegertracing/jaeger
cd $GOPATH/src/github.com/jaegertracing/jaeger
make install
cd examples/
go run ./main.go all
```

Then open http://127.0.0.1:8080


[hotrod-tutorial]: https://medium.com/@YuriShkuro/take-opentracing-for-a-hotrod-ride-f6e3141f7941
