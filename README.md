grafana
========

Ansible role to install grafana front-end.

Requirements
------------

Tested on Anbsible 1.8

Role Variables
--------------
    grafana_online_install: true                        # Whether or not to perform an online installation by downloading the installer
    grafana_installer_path: /tmp/grafana-1.9.1.tar.gz   # Where to find the installer for an offline installation
    grafana_version: 1.9.1                              # The version of grafana to install
    grafana_base_install_dir: /apps                     # Where to install grafana 
    grafana_influxdb_url: https://grafana/db            # The url for influxdb (accesible to users of Kibana)
    grafana_metrics_db: metrics                         # Name of the influxdb storing metrics
    grafana_dashboard_db: dashboard                     # Name of the influxdb storing dashboards
    grafana_metrics_db_user: root                       # Metrics db user
    grafana_metrics_db_password: root                   # Metrics db password
    grafana_dashboard_db_user: root                     # Dashboard db user
    grafana_dashboard_db_password: root                 # Dashboard db password
    grafana_healthcheck_url:                            # Expected healthcheck request
    grafana_healthcheck_file:                           # File to return as response to healthcheck
    grafana_healthcheck_content:                        # Content of http response
    grafana_htpasswd_files_path:                        # Where to find grafana.htpasswd
    grafana_purge_htpasswd: false                       # Delete htpasswd files 
    grafana_read_users:                                 # List of user hashes with read access (Requires python-passlib)
      guest:
        username: guest
        password: password
    grafana_write_users:                                # List of user hashes with write access (Requires python-passlib)
      first_last:
        username: lastf
        password: secret
    grafana_admin_users:
      first_last:
        username: admin_username
        password: more_secret

Dependencies
------------

nginx # Calls 'restart nginx' handler when configuration is created or modified

Example Playbook
-------------------------

    - hosts: all
      sudo: yes
      roles:
         - nginx
         - grafana

License
-------

MIT

Author Information
------------------

Jon Hadfield
