# Ansible Role Icescrum

This Ansible role installs and configures Icescrum (Official website: https://www.icescrum.com/).

By default this role installs the version V7 with a _jar_ setup. But you can choose the old version V6 (not recommanded) and/or a _war_ and tomcat setup.

## Table of contents
* [Prerequisites](#prerequisites)
* [Usage](#usage)
* [Example Playbook](#example-playbook)
* [Main variables](#main-variables)
	* [Mandatory](#mandatory)
	* [Recommended](#recommended)
	* [Optionnal](#optionnal)
* [Java options](#java-options)
* [Mail variables](#mail-variables)
* [LDAP variables](#ldap-variables)
* [Project variables](#project-variables)
* [Users variables](#users-variables)
* [Alerts variables](#alerts-variables)
* [War setup](#war-setup)
	* [Tomcat version](#tomcat-version)
	* [Tomcat proxy server](#tomcat-proxy-server)

## Prerequisites

* java 7, java 8 is recommended for Icescrum v7
* Mysql
* tomcat7, tomcat8 recommended for Icescrum v7 (Only for a war installation)

## Usage

    http://<host>:<port>/<context>
    http://localhost:8080/icescrum

Initial credentials are `admin / adminadmin!` . Do not forget to change it!

## Example Playbook

    - hosts: servers
      roles:
      - role: ansible-role-icescrum
        icescrum_appID: '726bafab-bcde-f1f2-abcd-f5e4d5c4b2a19'
        icescrum_scheme: 'https'
        icescrum_host: 'icescrum.company.com'
        icescrum_db_password: 'oloc4ever'

## Main variables

### Mandatory

    icescrum_appID: Add server ID file named _appID.txt_
    icescrum_license_key: Add iceScrum Pro Key.
    icescrum_host: Complete _grails.serverURL_ with the _\<host\>_ name to set a specific site location.

### Recommended

    icescrum_db_password: 'ic3scrum'

### Optionnal

    icescrum_scheme: 'http' or 'https'
    icescrum_port: '8080'
    icescrum_context: 'icescrum'
    icescrum_work_dir: '/tmp' It is where the embedded Tomcat webapps and work directory are created.
    icescrum_create_default_admin: 'true' or 'false'. False provide a setup wizard.
    icescrum_db_user: 'icescrum'
    icescrum_version: 'v7' [or the previous 'v6'].

## Java options

_For jar arguments or Catalina options._

    icescrum_xmx: 1024m
    icescrum_xms: 512m (optionnal)
    icescrum_maxpermsize: 256m (optionnal)
    icescrum_timezone: 'UTC' (optionnal)
    icescrum_java_extra_args: '-Dfoo=bar' (optionnal)

## Mail variables

To enable mail settings, turn `icescrum_mail_enable` into `True` and override with your own settings:

    icescrum_mail_enable: True
    icescrum_mail_host: "smtp.company.com"
    icescrum_mail_port: 465
    icescrum_mail_username: "username@company.com"
    icescrum_mail_password: "mypassword"
    icescrum_mail_auth: ''

**icescrum_mail_auth**: '', 'TLS', or 'SSL'

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

## War setup

### Tomcat version

There are some differences between tomcat `server.xml` version 7 and 8. You need to setup this parameter to configure the right listener.

    icescrum_tomcat_version: '8' [or the previous '7']

### Tomcat proxy server

To enable proxy settings, turn `icescrum_tomcat_proxy_active` int `True` and override with your own settings:

    icescrum_tomcat_proxy_server: icescrum.company.com
    icescrum_tomcat_proxy_port: 443

## License

MIT

## Author Information

This role was created in 2016 by Olivier Locard on the behalf of Deveryware.

