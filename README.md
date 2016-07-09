# docker-alp-powerdns
A simple docker powerdns container using alpine as the base OS and compiling latest version of powerdns

## backend modules included:
the following backend modules are compiled in:
```
- gmysql
- remote
- pipe
```
[Full List of Backends](https://doc.powerdns.com/md/authoritative/#backend-capibilities)

## run with config file:
This container will not run without a config file. Create one and supply it during runtime.
```
docker run --name powerdns \
  -v /local/path/pdns.conf:/usr/local/etc/pdns.conf:ro \
  -p 53:53 \
  -p 53:53/udp \
  gbolo/powerdns
```
