# Ansible Role Icescrum

## Prerequisites

* java 7, java 8 is recommended for Icescrum v7
* Mysql
* tomcat7, tomcat8 recommended for Icescrum v7

## Usage

    http://<server>:<port>/<context>
    http://localhost:8080/icescrum

Initial credentials are `admin / adminadmin!` . Do not forget to change it!

## Example Playbook

    - hosts: servers
      roles:
      - role: ansible-role-icescrum
        icescrum_appID: '726bafab-bcde-f1f2-abcd-f5e4d5c4b2a19'
        icescrum_scheme: 'https'
        icescrum_server: 'icescrum.company.com'
        icescrum_db_password: 'oloc4ever'

## Main variables

### Mandatory

    icescrum_appID: Add server ID file named _appID.txt_
    icescrum_license_key: Add iceScrum Pro Key.
    icescrum_server: Complete _grails.serverURL_ with the _\<server\>_ name to set a specific site location.

### Recommended

    icescrum_db_password: 'ic3scrum'

### Optionnal

    icescrum_version: 'v7' [or the previous 'v6'].
    icescrum_tomcat_version: '8' [or the previous '7']
    icescrum_create_default_admin: 'true' or 'false'. False provide a setup wizard.
    icescrum_scheme: 'http' or 'https'
    icescrum_db_user: 'icescrum'

## Mail variables

To enable mail settings, turn `icescrum_mail_enable` into `True` and override with your own settings:

    icescrum_mail_enable: True
    icescrum_mail_host: "smtp.company.com"
    icescrum_mail_port: 465
    icescrum_mail_username: "username@company.com"
    icescrum_mail_password: "mypassword"
    icescrum_mail_auth: ''

**icescrum_mail_auth**: '', 'TLS', or 'SSL'

## Proxy server

To enable proxy settings, turn `icescrum_tomcat_proxy_active` int `True` and override with your own settings:

    icescrum_tomcat_proxy_server: icescrum.company.com
    icescrum_tomcat_proxy_port: 443

## LDAP variables

To enable LDAP configuration, put your own settings:

    icescrum_ldap_enable: True
    icescrum_ldap_server: 'ldaps://ldap.company.com:636'
    icescrum_ldap_manager_dn: 'cn=admin,dc=company,dc=com'
    icescrum_ldap_manager_password: 'ThouShallNotPass'

You can override the default settings below:

    icescrum_ldap_search_base: ''
    icescrum_ldap_search_filter: '(uid={0})'
    icescrum_ldap_search_subtree: 'true'
    icescrum_ldap_attribute_first_name: 'givenName'
    icescrum_ldap_attribute_last_name: 'sn'
    icescrum_ldap_attribute_mail: 'mail'
    icescrum_ldap_ignore_result_exception: 'false'
    icescrum_anonymous_no_connection: 'false'

## Project variables

_Not available in Icescrum v6._

You can override the default settings below:

    icescrum_project_creation_enable: 'true'
    icescrum_project_export_enable: 'true'
    icescrum_project_import_enable: 'true'
    icescrum_project_private_default: 'false'
    icescrum_project_private_enable: 'true'

## Users variables

_Not available in Icescrum v6._

You can override the default settings below:

    icescrum_gravatar_enable: 'false'
    icescrum_registration_enable: 'true'
    icescrum_invitation_enable: 'false'
    icescrum_login_retrieve_enable: 'true'
    icescrum_sessionTimeoutSeconds: 1800

## Alerts variables

_Not available in Icescrum v6._

You can override the default settings below:

    icescrum_alerts_enable: 'true'
    icescrum_alerts_errors_to: "dev@icescrum.org"
    icescrum_alerts_subject_prefix: "[icescrum]"
    icescrum_alerts_default_from: "webmaster@icescrum.org"

## Catalina options

_Only for tomcat installation_

    icescrum_catalina_opts_xmx: 1024m
    icescrum_catalina_opts_xms: 512m (optionnal)
    icescrum_catalina_opts_maxpermsize: 256m (optionnal)
    icescrum_catalina_opts_timezone: 'UTC'

## License

MIT

## Author Information

This role was created in 2016 by Olivier Locard on the behalf of Deveryware.

