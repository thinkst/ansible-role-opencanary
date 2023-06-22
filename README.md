Role Description
=========

Installs [Thinkst OpenCanary](https://github.com/thinkst/opencanary) and configures options.

Example Playbooks
----------------

### Install from Github Branch

    - hosts: canaries
      roles:
        - role: ansible-role-opencanary
          vars:
            opencanary_version: master
            install_source: github
            portscan_enabled: "true"
            ssh_enabled: "true"
            ssh_port: 2222

### Install from PyPi.Org

    - hosts: canaries
      roles:
        - role: ansible-role-opencanary
          vars:
            opencanary_version: 0.7.1
            portscan_enabled: "true"
            mssql_enabled: "true"
            smb_enabled: "true"
            samba_share: "E$"

Role Variables
--------------

| **Name**                          | **Default Value**                | **Description**
| --------------------------------- | -------------------------------- | ------------------------
| `opencanary_install_dir`          | /opt/opencanary                  | Install directory for opencanary virtual environment.
| `opencanary_version`              | latest                           | Specifies the version of OpenCanary to install from PyPi.org/GitHub Tag/Branch.
| `install_source`                  | pypi                             | Specifies where to get the install from PyPi.org or GitHub.
| `github_src_dir`                  | /opt/opencanary_src              | Directory to clone git repo to and build src.
| `device_node_id`                  | opencanary-{{ ansible-hostname}} | OpenCanary device node id.
| `ip_ignorelist`                   | N/A                              | CIDR space delimited list of IP addresses.
| `git_enabled`                     | false                            | Enable git canary.
| `git_port`                        | 9418                             | Port for git canary.
| `ftp_enabled`                     | false                            | Enable ftp canary.
| `ftp_port`                        | 21                               | Port for ftp canary.
| `ftp_banner`                      | FTP Server Ready                 | Banner for ftp canary.
| `http_banner`                     | Apache/2.2.22 (Ubuntu)           | Banner for http canary.
| `http_enabled`                    | false                            | Enable http canary.
| `http_port`                       | 80                               | Port for http canary.
| `http_skin`                       | basicLogin                       | Skin to use for http canary. (basicLogin, nasLogin)
| `https_enabled`                   | false                            | Enable https canary.
| `https_port`                      | 443                              | Port for https canary.
| `https_skin`                      | basicLogin                       | Skin to use for https canary.
| `https_certificate`               | N/A                              | Certificate for https canary.
| `https_key   `                    | N/A                              | Key for certificate for https canary.
| `httpproxy_enabled`               | false                            | Enable http proxy canary.
| `httpproxy_port`                  | 8080                             | Port for http proxy canary.
| `httpproxy_skin`                  | ms-isa                           | Skin to use for http proxy canary. (snort, ms-isa)
| `logger_syslog_address`           | N/A                              | Syslog address/domain name to send logs.
| `logger_syslog_port`              | 514                              | Port to use for syslog logging.
| `logger_file_filename`            | /var/log/opencanary.log          | File path/name of local log.
| `smtp_mailhost`                   | N/A                              | Mail server to use.
| `smtp_port`                       | 25                               | SMTP port to mail server.
| `smtp_from_addr`                  | N/A                              | From address.
| `smtp_to_addr`                    | N/A                              | To Address.
| `smtp_subject`                    | OpenCanary Alert                 | Email subject.
| `slack_webhook_url`               | N/A                              | Incoming Slack Webhook URL for Slack Alerts.
| `teams_webhook_url`               | N/A                              | Incoming Teams Webhook URL for Teams Alerts.
| `webhook_url`                     | N/A                              | Generic Webhook URL.
| `webhook_method`                  | POST                             | HTTP method to use (GET, POST, PUT).
| `webhook_data`                    | '{"message": "%(message)s"}'     | Data to be sent to webhook.
| `webhook_status_code`             | 200                              | HTTP status code that is expected for a success.
| `webhook_ignore`                  | N/A                              | List of strings that will not emit any log that contains the pattern. ie "192.0.2."
| `portscan_enabled`                | false                            | Enable port scan canary.
| `portscan_ignore_localhost`       | false                            | Disables portscan for localhost.
| `portscan_logfile`                | /var/log/kern.log                | Log file scanned by port scan canary.
| `portscan_synrate`                | 5                                | SYN rate for port scan canary.
| `portscan_nmaposrate`             | 5                                | Nmap OS rate for port scan canary.
| `portscan_lorate`                 | 3                                | LO rate for port scan canary.
| `smb_auditfile`                   | /var/log/samba-audit.log         | Samba log for samba canary to watch.
| `smb_enabled`                     | false                            | Enable samba canary.
| `samba_workgroup`                 | WORKGROUP                        | Samba workgroup name.
| `samba_server_string`             | N/A                              | Samba server string.
| `samba_netbios_name`              | {{ ansible_hostname }}           | Netbios name for Samba server.
| `samba_share`                     | personal                         | Samba share name.
| `samba_comment`                   | Personal docs                    | Samba share comment.
| `samba_path`                      | /opt/{{ samab_share }}           | Samba path that houses the share.
| `mysql_enabled`                   | false                            | Enable mysql canary.
| `mysql_port`                      | 3306                             | Port to use for mysql canary.
| `mysql_banner`                    | 5.5.43-0ubuntu0.14.04.1          | Banner for mysql canary.
| `ssh_enabled`                     | false                            | Enable ssh canary.
| `ssh_port`                        | 22                               | Port to use for ssh canary.
| `ssh_banner`                      | SSH-2.0-OpenSSH_5.1p1 Debian-4   | Banner for ssh canary.
| `redis_enabled`                   | false                            | Enable redis canary.
| `redis_port`                      | 6379                             | Port to use for redis canary.
| `rdp_enabled`                     | false                            | Enable rdp canary.
| `rdp_port`                        | 3389                             | Port to use for rdp canary.
| `sip_enabled`                     | false                            | Enable sip canary.
| `sip_port`                        | 5060                             | Port to use for sip canary.
| `snmp_enabled`                    | false                            | Enable snmp canary.
| `snmp_port`                       | 161                              | Port to use for snmp canary.
| `ntp_enabled`                     | false                            | Enable ntp canary.
| `ntp_port`                        | 123                              | Port to use for ntp canary.
| `tftp_enabled`                    | false                            | Enable tftp canary.
| `tftp_port`                       | 69                               | Port to use for tftp canary.
| `tcpbanner_maxnum`                | 10                               | Max number of connections to tcpbanner canary.
| `tcpbanner_enabled`               | false                            | Enable tcpbanner canary.
| `tcpbanner_1_enabled`             | false                            | Enable tcpbanner_1 canary.
| `tcpbanner_1_port`                | 8001                             | Port for tcpbanner_1 canary.
| `tcpbanner_1_datareceivedbanner`  | N/A                              | Data received banner for tcpbanner_1 canary.
| `tcpbanner_1_initbanner`          | N/A                              | Init banner for tcpbanner_1 canary.
| `tcpbanner_1_alertstring_enabled` | false                            | Enable alert string for tcpbanner_1 canary.
| `tcpbanner_1_alertstring`         | N/A                              | Alert string for tcpbanner_1 canary.
| `tcpbanner_1_keep_alive_enabled`  | false                            | Enable keep alive for tcpbanner_1 canary.
| `tcpbanner_1_keep_alive_secret`   | N/A                              | Keep alive secret for tcpbanner_1 canary.
| `tcpbanner_1_keep_alive_probes`   | 11                               | Keep alive probes for tcpbanner_1 canary.
| `tcpbanner_1_keep_alive_interval` | 300                              | Keep alive interval for tcpbanner_1 canary.
| `tcpbanner_1_keep_alive_idle`     | 300                              | Keep alive idle for tcpbanner_1 canary.
| `telnet_enabled`                  | false                            | Enable telnet canary.
| `telnet_port`                     | 23                               | Port to use for telnet canary.
| `telnet_banner`                   | N/A                              | Banner for telnet canary.
| `mssql_enabled`                   | false                            | Enable mssql canary.
| `mssql_version`                   | 2012                             | Version of MSSQL to emulate with mssql canary.
| `mssql_port`                      | 1433                             | Port to use for mssql canary.
| `vnc_enabled`                     | false                            | Enable vnc canary.
| `vnc_port`                        | 5000                             | Port to use for vnc canary.


License
-------

MIT
