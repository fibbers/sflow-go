# sflow-go
GoLang tools for Sflow, originally from https://github.com/wimtie/sflow-go

# Building

Inside `sflow-go` directory:

```
$ export GOPATH=$GOPATH:`pwd`
$ go get github.com/influxdb/influxdb/client
$ go build sflux
```

An executable `sflux` should now be built.

# Running

If you run this on a host that receives sflow data on port 6343 and the same
host runs Influxdb, you can run something like this to insert sflow counter
stats into Influxdb:

```
$ sflowtool -p 6343 -l | grep CNTR | ts %s | sflux -d sflow -loglevel 3
```

For `sflowtool`, see https://github.com/kplimack/sflowtool.
