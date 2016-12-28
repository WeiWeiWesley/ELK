FROM elasticsearch:5

ENV ES_JAVA_OPTS="-Des.path.conf=/etc/elasticsearch"

CMD ["-E", "network.host=127.0.0.1", "-E", "discovery.zen.minimum_master_nodes=1"]
