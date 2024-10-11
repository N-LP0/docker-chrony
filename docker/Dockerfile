FROM alpine:latest

COPY entrypoint /usr/local/bin/
RUN set -eux; \
  apk add --update --no-cache \
  chrony \
  sudo;\
  chmod a+x /usr/local/bin/entrypoint; \
  sed -i '/# %sudo/c chrony ALL=(ALL:ALL) NOPASSWD: /usr/sbin/chronyd' /etc/sudoers;

USER chrony
EXPOSE 123/udp

ENTRYPOINT [ "entrypoint" ]
