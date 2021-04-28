# Telegraf output plugin 

** DateTime changed to DateTime64(3) and import of clickhouse fixed

## 1. How to use

## 1.1. add plugin files to telegraf repository.

```bash
# mkdir -p telegraf/plugins/outputs/clickhouse
# cp client.go metrics.go register.go telegraf/plugins/outputs/clickhouse
```

### 1.2. Enable this plugin

Append plugin into plugins/outpus/all/all.go

```bash
        _ "github.com/influxdata/telegraf/plugins/outputs/socket_writer"
        _ "github.com/influxdata/telegraf/plugins/outputs/stackdriver"
        _ "github.com/influxdata/telegraf/plugins/outputs/wavefront"
+       _ "github.com/influxdata/telegraf/plugins/outputs/clickhouse"
)
```

### 1.3. build telegraf

```bash
# cd telegraf
# make
```

### 1.4. update telegraf.conf

append follow lines.

```ini
[[outputs.clickhouse]]
	user = "default"
	password = ""
        addr = "127.0.0.1"
        port = 9000
        database = "telegraf"
        tablename = "metrics"
	write_timeout = 10
	debug = false
```
