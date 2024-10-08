FROM alpine:3.20.3

COPY entrypoint /usr/local/bin/
RUN apk add --update --no-cache chrony &&\
chmod u+x /usr/local/bin/entrypoint

EXPOSE 123/udp

ENTRYPOINT [ "entrypoint" ]
