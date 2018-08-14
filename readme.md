# rhsatellite_install_master

## Description:

Install an instance of RedHat Satellite 6 along with minimum configuration
(See role **rhsatellite_configure_master** for additional configuration role)

_Note: Still work in progress_

## Behaviour:

**Feature:** Installs a Satellite 6 server  
- **Given** a VM of capable size and power is available
- **Given** the connection details to the VM are known
- **Given** valid RedHat subscription is available
- **When** the install is executed
- **Then** subscriptions are attached
- **Then** pre-requisite checks are run
- **Then** Red Hat Satellite is installed
- **Then** basic configuration is carried out

## Configuration:

Common variables used by this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **amos_proxy_host_name**  | Proxy server address  | 192.168.22.33 |
| **amos_proxy_port**  | Proxy server port number  |  3128 |
| **redhat_user** | Red Hat user name |  |
| **redhat_pass** | Red Hat user password | |
| **redhat_activationkey** | Red Hat activation key | |
| **redhat_organization_id** | Red Hat Organisation ID |  |
| **redhat_pool_ids** | Red Hat pool IDs |  |

Variables specific to this role:

| Variable  | Description  | Example  | 
|---|---|---|
| **satins_hostname**  | Host FQDN  |  satellite-x123456.mydomain.com |
| **satins_admin_password**  |  Password for Satellite admin user | redhat123 |
| **satins_initial_organization**  | Organisation name. | Default Organization |
| **satins_initial_location**  | Initial location | Default Location |
| **satins_proxy_url**  | Proxy server url (optional) | http://192.168.10.10  |
| **satins_proxy_port**  | Proxy server port number (optional) | 3128  |

## Usage:

How to invoke the role from a playbook:

```yaml
- name: Installs Red Hat Satellite
  include_role:
    name: rhsatellite_install_master
  vars:
    satins_hostname: 'satellite-x123456.mydomain.com'
    satins_admin_password: 'redhat123'
    satins_initial_organization: 'Widget and Gadget Co.'
    satins_initial_location: 'United Kingdom'
```

Note: add common variables to the `vars` list as required.