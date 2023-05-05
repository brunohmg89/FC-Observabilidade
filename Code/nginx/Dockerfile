FROM nginx:latest
RUN rm -f /var/log/nginx/access.log && rm -f /var/log/nginx/error.log
COPY default.conf /etc/nginx/conf.d/default.conf

#RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.13.0-amd64.deb && \
#    dpkg -i filebeat-7.13.0-amd64.deb

# RUN curl -L -O https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-8.7.1-linux-x86_64.tar.gz && \
#     tar xzvf elastic-agent-8.7.1-linux-x86_64.tar.gz && \
#     cd elastic-agent-8.7.1-linux-x86_64 && \
#     sudo ./elastic-agent install -f --url=https://8ecd9cd783ee4826bde62ccab4dc84e0.fleet.us-east-1.aws.found.io:443 --enrollment-token=blh1YTVvY0JFdE8xanFURWwzLUY6eTNmWXN4SmdSLWE2d3JmaUxDOFdPZw==

COPY filebeat.yml /etc/filebeat/filebeat.yml
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x entrypoint.sh
ENTRYPOINT [ "/entrypoint.sh" ]