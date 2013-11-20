# Puppet OpenSUSE repositories module

This module adds and imports GPG keys for repositories
from OpenSUSE (http://download.opensuse.org/repositories).

### Requirements

Module has been tested on:

* Puppet 3.3
* SLES 11 SP3

Required modules:

* stdlib (https://github.com/puppetlabs/puppetlabs-stdlib)
* zypprepo (https://github.com/deadpoint/puppet-zypprepo)

# Quick Start

Add repository and import mirrored GPG key. Example:

```puppet
opensuse_repo { 'systemsmanagement:/puppet':
  enabled => 0,
}
```

Full configuration options:

```puppet
opensuse_repo { name:
  enabled      => 0|1|absent,  # enable state
  descr        => '...',       # repository description
  urlprefix    => 'http://download.opensuse.org/repositories',
  baseurl      => '...',       # custom repository URL
  platform     => '...',       # custom repository platform
  gpgkey       => '...',       # custom GPG key URL
  local_gpgkey => true|false,  # use GPG key from module
  gpgcheck     => 0|1,         # check GPG signatures?
  autorefresh  => 0|1,         # autorefresh repo. metadata?
  keeppackages => 0|1,         # keep downloaded files?
  type         => '...',       # repository type (format)
}
```

Class wrapper for adding multiple repositories at time.

```puppet
class { 'opensuse_repo::multiple':
  repos   => [ ... ],
  options => { ... }
}
```

Example: 

```puppet
class { 'opensuse_repo::multiple':
  repos => ['systemsmanagement:/puppet', 'filesystems'],
}
```

***

CERIT Scientific Cloud, <support@cerit-sc.cz>
