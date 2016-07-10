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
docker run -d --name powerdns \
  -v /local/path/pdns.conf:/usr/local/etc/pdns.conf:ro \
  -p 53:53 \
  -p 53:53/udp \
  -p 8081:8081 \
  gbolo/powerdns
```
version **4.0.0-rc2** also available for testing with this image: `gbolo/powerdns:4.0.0-rc2`

## example config
pdns.conf
```
### Backend config
launch=gmysql
gmysql-host=10.x.x.x
gmysql-dbname=powerdns
gmysql-user=powerdns
gmysql-password=powerdns
gmysql-port=3306

### REST API (3.x)
experimental-json-interface=yes
experimental-api-key=changeme
webserver=yes
webserver-address=0.0.0.0

### OTHER
default-soa-name=ns.example.com
default-soa-mail=root.example.com

```
