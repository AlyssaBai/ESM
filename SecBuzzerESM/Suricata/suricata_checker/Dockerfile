from alpine:3

RUN set -ex \
    && echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
    && apk add --update --no-cache tcpreplay jq curl tini

CMD mkdir -p /cron && cp /image/root /cron/ && chmod 0644 /cron \
  && crond -b -c /cron -L /var/log/cron.log && touch /var/log/cron.log && tail -F /var/log/cron.log

ENTRYPOINT ["/sbin/tini", "--"]

# CMD "sleep" "infinity"
CMD mkdir -p /cron && cp /image/root /cron/ && chmod 0644 /cron \
  && crond -b -c /cron && touch /var/log/cron.log && tail -F /var/log/cron.log