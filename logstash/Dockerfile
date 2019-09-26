FROM logstash:7.3.2

# Add your logstash plugins setup here
# Example: RUN logstash-plugin install logstash-filter-json
RUN logstash-plugin install logstash-input-file
RUN logstash-plugin install logstash-input-redis
RUN logstash-plugin install logstash-filter-json
RUN logstash-plugin install logstash-filter-grok
RUN logstash-plugin install logstash-filter-mutate
RUN logstash-plugin install logstash-filter-date
RUN logstash-plugin install logstash-filter-sleep
RUN logstash-plugin install logstash-output-stdout