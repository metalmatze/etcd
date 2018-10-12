# Prometheus Monitoring Mixin for etcd

> NOTE: This project is *alpha* stage. Flags, configuration, behaviour and design may change significantly in following releases.

A set of customisable Prometheus alerts for etcd.

Instructions for use are the same as the [kubernetes-mixin](https://github.com/kubernetes-monitoring/kubernetes-mixin).

## Background

* For more information about monitoring mixins, see this [design doc](https://docs.google.com/document/d/1A9xvzwqnFVSOZ5fD3blKODXfsat5fg6ZhnKu9LK3lB4/edit#).

## Testing alerts

Make sure to have [jsonnet](https://jsonnet.org/) and [gojsontoyaml](https://github.com/brancz/gojsontoyaml) installed.

First you need to compile the mixin to a YAML file for the promtool to read it:
```
jsonnet -e '(import "mixin.libsonnet").prometheusAlerts' | gojsontoyaml > mixin.yaml
```

Now you can run the unit test with:
```
promtool test rules test.yaml
```
