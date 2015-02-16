# Let's Chat - Kerberos Plugin

Add Kerberos authentication to [Let's Chat](http://sdelements.github.io/lets-chat/).

## Node 0.10.x required!
[See ticket for more information](https://github.com/sdelements/lets-chat-kerberos/issues/1)

## Installation

### Prerequisites

###### Mac
Kerberos headers are shipped with Mac OS X.

###### Linux
You'll need to install the Kerberos 5 development headers package. It may be called ```krb5-dev``` or ```libkrb5-dev```.

###### Windows
You'll need to install [MIT Kerberos for Windows](http://web.mit.edu/kerberos/dist/#kfw-4.0) (with SDK option checked).

### Install

```
npm install lets-chat-kerberos
```

### Configure

Add these settings to your ```settings.yml``` file:

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
      server_certs: []
      bind_options:
        bindDN:
        bindCredentials:
      search:
        base:
        opts:
          scope: one
          filter: (uid={{username}})
          attributes: []
      field_mappings:
        uid: uid
        firstName: givenName
        lastName: sn
        displayName: givenName
        email: mail
```
