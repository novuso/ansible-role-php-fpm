# Ansible Role: PHP FPM

[![Ansible Galaxy](http://img.shields.io/badge/galaxy-novuso.php--fpm-000000.svg)](https://galaxy.ansible.com/list#/roles/3863)
[![MIT License](http://img.shields.io/badge/license-MIT-003399.svg)](http://opensource.org/licenses/MIT)
[![Build Status](https://travis-ci.org/novuso/ansible-role-php-fpm.svg)](https://travis-ci.org/novuso/ansible-role-php-fpm)

An Ansible role that manages PHP FPM on Ubuntu 14.04

## Requirements

None

## Role Variables

Ansible variables are listed here along with their default values:

`php_fpm_packages` is a list of packages that are managed for this role. Each
entry in the list may designate:

* **name** *required*
* **state** (default present)

By default, the following packages are used:

    php_fpm_packages:
    - name: "php5-fpm"

`php_fpm_server` sets the HTTP server for PHP FPM. It can be either "nginx" or
"apache".

    php_fpm_server: "nginx"

`php_fpm_user` sets the user for the "www" pool.

    php_fpm_user: "www-data"

`php_fpm_group` sets the group for the "www" pool.

    php_fpm_group: "www-data"

`php_fpm_listen` sets the listen setting for the "www" pool.

    php_fpm_listen: "127.0.0.1:9000"

`php_fpm_short_open_tag` sets the `short_open_tag` setting.

    php_fpm_short_open_tag: "Off"

`php_fpm_expose_php` sets the `expose_php` setting.

    php_fpm_expose_php: "Off"

`php_fpm_max_execution_time` sets the `max_execution_time` setting.

    php_fpm_max_execution_time: "0"

`php_fpm_max_input_time` sets the `max_input_time` setting.

    php_fpm_max_input_time: "60"

`php_fpm_memory_limit` sets the `memory_limit` setting.

    php_fpm_memory_limit: "512M"

`php_fpm_error_reporting` sets the `error_reporting` setting.

    php_fpm_error_reporting: "E_ALL & ~E_DEPRECATED & ~E_STRICT"

`php_fpm_display_errors` sets the `display_errors` setting.

    php_fpm_display_errors: "Off"

`php_fpm_display_startup_errors` sets the `display_startup_errors` setting.

    php_fpm_display_startup_errors: "Off"

`php_fpm_track_errors` sets the `track_errors` setting.

    php_fpm_track_errors: "Off"

`php_fpm_html_errors` sets the `html_errors` setting.

    php_fpm_html_errors: "Off"

`php_fpm_variables_order` sets the `variables_order` setting.

    php_fpm_variables_order: "GPCS"

`php_fpm_request_order` sets the `request_order` setting.

    php_fpm_request_order: "GP"

`php_fpm_post_max_size` sets the `post_max_size` setting.

    php_fpm_post_max_size: "8M"

`php_fpm_default_mimetype` sets the `default_mimetype` setting.

    php_fpm_default_mimetype: "text/html"

`php_fpm_default_charset` sets the `default_charset` setting.

    php_fpm_default_charset: "UTF-8"

`php_fpm_upload_max_filesize` sets the `upload_max_filesize` setting.

    php_fpm_upload_max_filesize: "10M"

`php_fpm_max_file_uploads` sets the `max_file_uploads` setting.

    php_fpm_max_file_uploads: "3"

`php_fpm_date_timezone` sets the `date.timezone` setting.

    php_fpm_date_timezone: "UTC"

`php_fpm_include_path` sets the `include_path` setting.

    php_fpm_include_path: ".:/usr/share/php"

`php_fpm_enable_includes` flags whether or not to enable the include path.

    php_fpm_enable_includes: true

`php_fpm_opcache_enable` sets the `opcache.enable` setting.

    php_fpm_opcache_enable: "0"

`php_fpm_opcache_memory_consumption` sets the `opcache.memory_consumption`
setting.

    php_fpm_opcache_memory_consumption: "64"

`php_fpm_opcache_interned_strings_buffer` sets the
`opcache.interned_strings_buffer` setting.

    php_fpm_opcache_interned_strings_buffer: "16"

`php_fpm_opcache_max_accelerated_files` sets the
`opcache.max_accelerated_files` setting.

    php_fpm_opcache_max_accelerated_files: "4000"

`php_fpm_opcache_validate_timestamps` sets the `opcache.validate_timestamps`
setting.

    php_fpm_opcache_validate_timestamps: "1"

`php_fpm_opcache_revalidate_freq` sets the `opcache.revalidate_freq` setting.

    php_fpm_opcache_revalidate_freq: "0"

`php_fpm_opcache_fast_shutdown` sets the `opcache.fast_shutdown` setting.

    php_fpm_opcache_fast_shutdown: "1"

`php_fpm_extra_settings` is a list of additional settings. Each entry in the
list may designate:

* **setting** the line to add to php.ini *required*
* **state** (default is present)

By default, no extra settings are used:

    php_fpm_extra_settings: []

## Dependencies

* novuso.php-ext

## Example Playbook

    ---
    - hosts: all
      vars:
      - php_fpm_error_reporting: "E_ALL"
      - php_fpm_display_errors: "On"
      - php_fpm_display_startup_errors: "On"
      roles:
      - novuso.php-ext
      - novuso.php-fpm

## License

This is released under the [MIT license](http://opensource.org/licenses/MIT).
