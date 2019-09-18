FROM elasticsearch:7.3.2

ENV ES_JAVA_OPTS="-Des.path.conf=/etc/elasticsearch"

CMD ["-E", "network.host=127.0.0.1", "-E", "discovery.zen.minimum_master_nodes=1"]