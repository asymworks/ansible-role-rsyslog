# Ansible Role: Asymworks Rsyslog

An Ansible Role that installs Rsyslog on Asymworks servers running Debian or Alpine Linux.

## Requirements

None

## Role Variables

Available variables are listed below, along with default values if applicable (see `defaults/main.yml`):

```yaml
rsyslog_enabled: true
syslog_server: logs.lan
syslog_port: 10514
```

Whether the remote `syslog` server is enabled and installe.  If enabled, logs are sent in RFC3164 format via UDP to the specified server and port so they can be parsed by e.g. Logstash or Graylog.

```yaml
rsyslog_hostname:
rsyslog_preserve_fqdn: true
```

Sets the hostname that Rsyslog reports.  If this is unset (the default), the Rsyslog default behavior will be used.  Set `rsyslog_preserve_fqdn` to `true` to have Rsyslog preserve the FQDN of the host, otherwise the short hostname will be sent.

## Role Facts

None

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  pre_tasks:
    include_role:
      name: asymworks.baseline
      tasks_from: pre-tasks.yml
  roles:
    asymworks.baseline
    asymworks.rsyslog
  post_tasks:
    include_role:
      name: asymworks.baseline
      tasks_from: post-tasks.yml
```

## License

MIT / BSD

## Author

This role was created in 2022 by Asymworks, LLC.
