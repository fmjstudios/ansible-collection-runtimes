# Ansible Role: OpenLiteSpeed + PHP

This role first installs the OpenLiteSpeed repositories, updates system packages, then installs the OLS web server and
accompanying PHP versions from the litespeed repositories.

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
ols:
  version: 1.7.16
  repo: "https://repo.litespeed.sh"
  package: openlitespeed
  service_name: lsws
  install_path: /usr/local/lsws

ols_config:
  listen_addr: "0.0.0.0"
  http_port: 80
  https_port: 443
  admin_emails:
    - admin@example.com
  log_level: DEBUG
  virtual_hosts:
    - domain: crank.delta4x4.net
      root: /home/openlitespeed/webapps/crank.delta4x4.net
      aliases:
        - www.$VH_NAME
      ssl:
        ssl_certificate: /etc/letsencrypt/certs/crank.delta4x4.net/cert.pem
        ssl_key: /etc/letsencrypt/certs/crank.delta4x4.net/cert.key
      user: lsadm
      group: lsadm
      admin_email: admin@example.com

php:
  version: 8.1
  dependencies:
    - mysql-client
  extensions:
    - common
    - dbg
    - igbinary
    - imap
    - ioncube
    - memcached
    - msgpack
    - opcache
    - pgsql
    - redis
    - sqlite3
    - tidy
    - apcu
    - curl
    - dev
    - imagick
    - intl
    - ldap
    - mysql
    - pear
    - pspell
    - snmp
    - sybase

```

## Dependencies

None.

## Example Playbook

```yaml
    - hosts: all
      roles:
        - role: delta4x4.runtimes.openlitespeed
          tags: [ runtime, openlitespeed ]
          vars:
          ols:
          # version: 1.7.16
          # ..
          ols_config:
          # listen_addr: "0.0.0.0"
          # ... 
          php:
          # version: 8.1
          # ...

```

## License

Proprietary

## Author Information

This role was created in 2023 by [Maximilian Gindorfer](https://fmj.dev).
