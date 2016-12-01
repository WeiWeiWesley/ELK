FROM logstash:5

# Add your logstash plugins setup here
# Example: RUN logstash-plugin install logstash-filter-json
RUN logstash-plugin install logstash-codec-es_bulk
RUN logstash-plugin install logstash-input-file
RUN logstash-plugin install logstash-filter-json
RUN logstash-plugin install logstash-filter-grok
RUN logstash-plugin install logstash-filter-mutate
RUN logstash-plugin install logstash-filter-date
