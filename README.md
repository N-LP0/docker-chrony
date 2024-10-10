# chrony

[hub.docker.com](https://hub.docker.com/r/nlp0/chrony)

## Run

```bash
docker run -d --restart unless-stopped \
-e NTP_SERVERS="ntp0.ntp-servers.net, ntp1.ntp-servers.net, ntp2.ntp-servers.net" \
-e NTP_POOLS="0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org" \
-e ALLOW_CIDR="192.168.0/24, 10.10.0/24" \
nlp0/chrony:latest
```

## Show chrony.conf

```bash
docker exec -i $(docker ps | grep nlp0/chrony | awk '{print $1}') cat /etc/chrony/chrony.conf
```

## Output

```conf
# default config

server ntp0.ntp-servers.net iburst
server ntp1.ntp-servers.net iburst
server ntp2.ntp-servers.net iburst
pool 0.pool.ntp.org iburst
pool 1.pool.ntp.org iburst
pool 2.pool.ntp.org iburst
pool 3.pool.ntp.org iburst
initstepslew 10 pool.ntp.org
driftfile /var/lib/chrony/chrony.drift
rtcsync
cmdport 0
allow 192.168.0/24
allow 10.10.0/24
```
