# Ansible Role: PHP

This role installs PHP at a specified version with FPM. It takes inspiration from [GitHub: injectedMonkey - ansible-role-php-fpm](https://github.com/injectedMonkey/ansible-role-php-fpm).

## Requirements

N/A

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

``` yaml
php:
  version: 8.1
  repositories:
    ppa:
      - ppa:ondrej/php
  packages:
    - cli
    - common
    - curl
    - fpm
    - mysql
    - xml
    - zip
    - gd
    - mbstring
    - apcu
    - opcache

php_memory_limit: 512M
php_allow_url_fopen: On
php_upload_max_filesize: 6M
php_max_execution_time: 60
php_date_timezone: Europe/Berlin

enabled_extensions:
  - curl
  - gd
  - mbstring
  - openssl
  - pdo_mysql

enabled_zend_extensions:
  - opcache
```

## Dependencies

None.

## Example Playbook

```yaml
    - hosts: all
      roles:
        - role: delta4x4.runtimes.php
          vars:
            # php:
              # version: 8.1
```

## License

Proprietary

## Author Information

This role was created in 2023 by [Maximilian Gindorfer](https://fmj.dev).
