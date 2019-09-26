Redis ELK
===

結合 reids & ELK 搜集分散式 log。適合想統一異質平台或已微服務化的系統使用。

僅需將目標 log RPUSH 至指定的 redis key，便可輕鬆地藉由 logstash 取出至 elasticserach 最後由 kibana 呈現。

