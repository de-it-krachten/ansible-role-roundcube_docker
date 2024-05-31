[![CI](https://github.com/de-it-krachten/ansible-role-roundcube_docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-roundcube_docker/actions?query=workflow%3ACI)


# ansible-role-wordpress_docker

Sets up a Roundcube Webmail instance using Docker.



## Dependencies

#### Roles
None

#### Collections
- community.docker

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8<sup>1</sup>
- RockyLinux 9<sup>1</sup>
- OracleLinux 8<sup>1</sup>
- OracleLinux 9<sup>1</sup>
- AlmaLinux 8<sup>1</sup>
- AlmaLinux 9<sup>1</sup>
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15<sup>1</sup>
- Debian 10 (Buster)<sup>1</sup>
- Debian 11 (Bullseye)<sup>1</sup>
- Debian 12 (Bookworm)<sup>1</sup>
- Ubuntu 18.04 LTS<sup>1</sup>
- Ubuntu 20.04 LTS<sup>1</sup>
- Ubuntu 22.04 LTS<sup>1</sup>
- Ubuntu 24.04 LTS
- Fedora 39<sup>1</sup>
- Fedora 40<sup>1</sup>
- Alpine 3<sup>1</sup>
- Docker dind (CI only)

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Location where to put files
# roundcube_docker_data: /export/docker/roundcube

# FQDN of the external server
# roundcube_fqdn: webmail.example.com

# Database type to use
roundcube_db_type: pgsql

# Name of the database server
roundcube_db_host: database

# Name of the database itself
roundcube_db_name: roundcube

# Name of the database user
roundcube_db_user: roundcube

# Password for the database user
roundcube_db_password: roundcube

# Server for nginx to connect to
roundcube_mail_host: webapp

# Roundcube web ports
roundcube_http_port: 80
roundcube_https_port: 443

# IMAP/SMTP server
roundcube_imap_host: localhost
roundcube_imap_port: 143
roundcube_smtp_host: localhost
roundcube_smtp_port: 25
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'wordpress_docker'
  hosts: all
  become: 'yes'
  vars:
    roundcube_docker_data: /export/docker/roundcube
    roundcube_fqdn: webmail.example.com
    roundcube_db_type: pgsql
    roundcube_db_host: database
    roundcube_db_name: roundcube
    roundcube_db_user: roundcube
    roundcube_db_password: roundcube
    roundcube_mail_host: webapp
    roundcube_https_port: 443
    roundcube_http_port: 80
    roundcube_imap_host: localhost
    roundcube_imap_port: 143
    roundcube_smtp_host: localhost
    roundcube_smtp_port: 25
  roles:
    - deitkrachten.openssl
  tasks:
    - name: Include role 'roundcube_docker'
      ansible.builtin.include_role:
        name: roundcube_docker
</pre></code>
