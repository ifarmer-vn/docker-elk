ARG ELK_VERSION

# https://github.com/elastic/logstash-docker
FROM docker.elastic.co/logstash/logstash:${ELK_VERSION}

# Add your logstash plugins setup here
# Example: RUN logstash-plugin install logstash-filter-json
ENV PLUGIN_BIN "/usr/share/logstash/bin/logstash-plugin"


RUN "$PLUGIN_BIN" install logstash-input-syslog
RUN "$PLUGIN_BIN" install logstash-filter-date
RUN "$PLUGIN_BIN" install logstash-filter-grok
RUN "$PLUGIN_BIN" install logstash-filter-useragent
RUN "$PLUGIN_BIN" install logstash-output-elasticsearch

COPY ./config /etc/logstash

CMD ["-f", "/etc/logstash/logstash.conf"]