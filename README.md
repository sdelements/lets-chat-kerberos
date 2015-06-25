# Let's Chat - Kerberos Plugin

Add Kerberos authentication to [Let's Chat](http://sdelements.github.io/lets-chat/).

## Installation

### Prerequisites

###### Mac
Kerberos headers are shipped with Mac OS X.

###### Linux
You'll need to install the Kerberos 5 development headers package. It may be called ```krb5-dev``` or ```libkrb5-dev```.

###### Windows
You'll need to install [MIT Kerberos for Windows](http://web.mit.edu/kerberos/dist/#kfw-4.0) (with SDK option checked).

This module depends on node-krb5, so installation instructions for that module should be taken into account. On Windows you must set the environment variable MITKRB5 to the MIT Kerberos home.

```
set MITKRB5=C:\Program Files\MIT\Kerberos
```

### Install

```
npm install lets-chat-ldap
npm install lets-chat-kerberos
```

### Configure

##### YAML

Add (and customize) these settings to your ```settings.yml``` file:

```yml
auth:
  kerberos:
    realm: example.com
    use_ldap_authorization: false

    # if use_ldap_authorization == true
    ldap:
      connect_settings:
        url: ldap://example.com
        tlsOptions:
          ca: ca.pem
      bind_options:
        bindDN:
        bindCredentials:
      search:
        base:
        opts:
          scope: one
          filter: (uid={{username}})
      field_mappings:
        uid: uid # LDAP unique ID
        username: uid # used for mention (@uid)
        firstName: givenName
        lastName: sn
        displayName: givenName
        email: mail
```

##### Environment Variables

Alternatively, configure using environment variables:

| YAML Path | Env Variable |
|-----------|--------------|
| | LCB_AUTH_KERBEROS_REALM |
| | LCB_AUTH_KERBEROS_USE_LDAP_AUTHORIZATION |
| | LCB_AUTH_KERBEROS_LDAP_CONNECT_SETTINGS_URL |
| | LCB_AUTH_KERBEROS_LDAP_CONNECT_SETTINGS_TLS_OPTIONS_CA |
| | LCB_AUTH_KERBEROS_LDAP_BIND_OPTIONS_BIND_DN |
| | LCB_AUTH_KERBEROS_LDAP_BIND_OPTIONS_BIND_CREDENTIALS |
| | LCB_AUTH_KERBEROS_LDAP_SEARCH_BASE |
| | LCB_AUTH_KERBEROS_LDAP_SEARCH_OPTS_SCOPE |
| | LCB_AUTH_KERBEROS_LDAP_SEARCH_OPTS_FILTER |
| | LCB_AUTH_KERBEROS_LDAP_FIELD_MAPPINGS_UID |
| | LCB_AUTH_KERBEROS_LDAP_FIELD_MAPPINGS_USERNAME |
| | LCB_AUTH_KERBEROS_LDAP_FIELD_MAPPINGS_FIRST_NAME |
| | LCB_AUTH_KERBEROS_LDAP_FIELD_MAPPINGS_LAST_NAME |
| | LCB_AUTH_KERBEROS_LDAP_FIELD_MAPPINGS_DISPLAY_NAME |
| | LCB_AUTH_KERBEROS_LDAP_FIELD_MAPPINGS_EMAIL |
