# Google Apps Delegate Admin installation

## What does it do?

1. Installs Google Apps Delegate Admin and all dependencies to /opt/
2. Sets up Apache2 with mod_wsgi to run the web server

## What do you have to do?

1. Check the defaults/main configuration
2. Change the variables according to how you want them, either in defaults/main or by setting vars in the play
3. Add your client_secret, see [here for info on generating](https://developers.google.com/api-client-library/python/guide/aaa_oauth#acquiring--client-ids-and-secrets)

## How can I use this role?

We can use this role to install a preconfigured version of Google Apps Delegate Admin to any Debian/Ubuntu/RedHat/CentOS server

For example we can pass the following settings:

```
#example-playbook.yml

- name: example
  hosts: delegateadminservers
  become: true
  vars: 
    - install_path: /opt/gapps-delegate-admin
    - gapps_delegate_client_secret_json: 'CLIENT_SECRET_JSON_CONTENT'
    - server_name: 'delegateadmin.domain.com'
    - gapps_delegate_admin_user: 'www-data'
    - gapps_delegate_admin_group: 'www-data'
  roles:
    - gapps-delegate-admin
```

``` ansible-playbook example-playbook.yml ```

## Compability

Tested on:

Debian 8 & CentOS 7
