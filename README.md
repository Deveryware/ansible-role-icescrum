# Ansible Role Icescrum

## Prerequisites

* java 7
* Mysql
* tomcat7

## Usage

    http://<server>

Initial credentials are `admin/admin`

## Example Playbook

    - hosts: servers
      roles:
      - role: ansible-role-icescrum
        icescrum_appID: '726bafab-bcde-f1f2-abcd-f5e4d5c4b2a19'
        icescrum_scheme: 'https'
        icescrum_server: 'icescrum.company.com'
        icescrum_db_password: 'oloc4ever'

## Main variables

**icescrum_appID**: Add server ID file named _appID.txt_

**icescrum_scheme**: 'http' or 'https'

**icescrum_server**: Complete _grails.serverURL_ with the _\<server\>_ name to set a specific site location.

**icescrum_db_user**: 'icescrum'

**icescrum_db_password**: 'ic3scrum'

## Mail variables

To enable mail settings, turn `icescrum_mail_enabled` into `True` and override with your own settings:

    icescrum_mail_enabled: True
    icescrum_mail_host: "smtp.company.com"
    icescrum_mail_port: 465
    icescrum_mail_username: "username@company.com"
    icescrum_mail_password: "mypassword"
    icescrum_mail_auth: ''

**icescrum_mail_auth**: '', 'TLS', or 'SSL'

## License

MIT

## Author Information

This role was created in 2016 by Olivier Locard on the behalf of Deveryware.

