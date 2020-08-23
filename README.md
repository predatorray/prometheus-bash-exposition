# github-prometheus-exporter

A command line tool to print [Prometheus exposition format](https://prometheus.io/docs/instrumenting/exposition_formats/) file.

## Example

```sh
prom-exposit --name http_requests_total --type counter --comment 'The total number of HTTP requests.' \
    --label method=post --label code=200 --timestamp 1395066363000 --value 1027 \
    --label method=post --label code=400 --timestamp 1395066363000 --value 3 \
    --name metric_without_timestamp_and_labels --value 12.47
```

The output will be

```txt
# HELP http_requests_total The total number of HTTP requests.
# TYPE http_requests_total counter
http_requests_total{method="post",code="200",} 1027 1395066363000
http_requests_total{method="post",code="200",method="post",code="400",} 3 1395066363000
# HELP metric_without_timestamp_and_labels 
# TYPE metric_without_timestamp_and_labels UNTYPED
metric_without_timestamp_and_labels 12.47
```