
|Gernel Setting|狀況|
|---|---|
|開啟UFW,allow SSH,Node_Exporter,SNMP|OK|
|關閉SWAP|OK|
|加入AD||
|限制特定 AD Group 登入||
|硬碟格式為 XFS|OK|
|timezone UTC -4|OK|
|對時方式 ntpdate 兩台主機 (每30分鐘不同台)|OK|
|mtr,ntpdate,tcpdump,snmp|OK|


|Network|狀況|
|---|---|
|Data Lan|*|
|雙網卡做LACP|OK|
|不設定 VLAN|OK|
|MTU 預設值|OK|
|Storage Lan|*|
|雙網卡做 MultiPath 連接 iSCSI||
|雙網卡不同 SUBNET||
|Storage iSCSI 會設定 CHAP||
|不設定 VLAN||
|MTU 設定為 Jumbo Frame||


|Kernel Tunning|狀況|
|---|---|
|open files = 10485676|*|
|root|OK|
|非root|OK|
|systemd的system跟user都要套用|OK|
|sysctl設定值|*|
|net.nf_conntrack_max = 262144|OK|
|fs.file-max = 10000000|OK|
|vm.overcommit_memory = 1|OK|
|vm.swappiness = 0|OK|
|net.core.somaxconn = 65535|OK|
|net.ipv4.tcp_max_syn_backlog = 65535|OK|
|net.ipv4.ip_local_port_range = 10000 65535|OK|
|net.ipv4.tcp_max_tw_buckets = 32768|OK|


|建置Elk|狀況|
|---|---|
|安裝elasticsearch＊3 做 cluster|OK|
|安裝kibana|OK|
|ubuntu安裝 filebeat 並將system log 吐到 elasticsearch||
|收集設備的syslog to logstash or fluentd 如沒有硬體可以收 可以收ubuntu syslog||
繪製 kibana dashboard||
|elasticsearch 告警 to slack||

|建置Prometheus|狀況|
|---|---|
|安裝prometheus|OK|
|安裝grafana|OK|  
|所有ubuntu 安裝node_exporter|OK| 
|prometheus收集所有node_exporter效能|OK| 
|grafana產生 dashboard 並加入ad|OK|
|設定alertmanager告警to slack||

|建置zabbix|狀況|
|---|---|
|安裝zabbix|OK|
|所有ubuntu 開啟 snmp v2, community name:cqcp|OK|
|繪製weathermap|OK|
|設定zabbix告警to slack||
