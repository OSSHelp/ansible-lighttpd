# lighttpd

[![Build Status](https://drone.osshelp.ru/api/badges/ansible/lighttpd/status.svg)](https://drone.osshelp.ru/ansible/lighttpd)

Ansible role for lighttpd installation and configuration.

## Usage (example)

```yaml
    - role: lighttpd
      lighttpd_confs_enabled:
        - 10-fastcgi
      lighttpd_server_modules:
        - mod_access
        - mod_alias
        - mod_compress
        - mod_redirect
```

## Available parameters

### Main

| Param | Default | Description |
| -------- | -------- | -------- |
| `lighttpd_setup` | `full` | Setup mode. See [OSSHelp KB article](https://oss.help/kb4895) |
| `lighttpd_global_params` | `See below` | Lighttpd.conf main configuration file parameter list |
| `lighttpd_server_modules` | `mod_(access|alias|compress|redirect)` | Plugins list |
| `lighttpd_src_conf_location` | `files/lighttpd/conf-available` | Directory with your custom configs |
| `lighttpd_copy_custom_conf` |  | Whether it is required to copy files from `lighttpd_src_conf_location` |
| `lighttpd_confs_enabled` |  | Creates symlinks from conf-available in conf-enabled |
| `lighttpd_server_status` | | Is it required to enable config for server-status location |

### lighttpd_global_params

List with parameters for lighttpd.conf.

| Param | Default |
| -------- | -------- |
| `server_document_root` | `/var/www/html` |
| `server_upload_dirs` | `/var/cache/lighttpd/uploads` |
| `server_errorlog` | `/var/log/lighttpd/error.log` |
| `server_pid_file` | `/var/run/lighttpd.pid` |
| `server_username` | `www-data` |
| `server_groupname` | `www-data` |
| `server_port` | `80` |
| `index_file_names` | `( "index.php", "index.html", "index.lighttpd.html" )` |
| `url_access_deny` | `( "~", ".inc" )` |
| `static_file_exclude_extensions` | `( ".php", ".pl", ".fcgi" )` |
| `compress_cache_dir` | `"/var/cache/lighttpd/compress/"` |
| `compress_filetype` | `( "application/javascript", "text/css", "text/html", "text/plain" )` |

## License

GPL3

## Author

OSSHelp Team, see <https://oss.help>
