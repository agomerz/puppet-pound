Pound reverse proxy module
==========================

Status
------
This module is in a fairly basic state right now, this is my first attempt at writing a real puppet module so please review the code before you put it into action. My goal is to support all features of pound in as clean and reusable a way as possible. 

Puppet-pound is heavilly inspired by the [CampToCamp bind] [1] module.

Features
--------
Manage a single /etc/pound/pound.cfg configuration, add entries for HTTP listeners and their backends.

Todo
----
* Rework the module a bit to follow best practice
* Add support for changing Global Directives (currently static defaults)
* Some kind of support for managing the service with the poundctl command might be good to have (maybe even essential)

Usage
-----
``` puppet
#node.pp
    pound::entry {
        'test' :
            listen_ip => '30.40.50.60',
            listen_port => '8888',
            listen_protocol => 'ListenHTTP',
            head_require => 'Host:.*stuff.myserver.com.*',
            backend_ip => '13.14.15.16',
            backend_port => '9999'
    }
    pound::entry {
        'test2' :
            listen_ip => '1.101.101.10',
            listen_port => '8828',
            listen_protocol => 'ListenHTTPS',
            head_require => 'Host:.*www.myserver.com.*',
            backend_ip => '14.14.14.14',
            backend_port => '9399'
    }
```
Copyright
---------
GPLv3 or later

[1]: https://github.com/camptocamp/puppet-bind        "CampToCamp Bind"
