LLNW collectd packaging for Debian/Ubuntu
=========================================

* Upstream:  git://git.tokkee.org/pkg-collectd
* gitweb: http://git.tokkee.org/?p=pkg-collectd.git

Requirements:
--------------

### Debian 7.x:

```bash
apt-get install build-essential autotools-dev libltdl-dev debhelper po-debconf dpatch bison flex pkg-config iptables-dev javahelper libcurl4-gnutls-dev  libcurl4-gnutls-dev  libcurl3-gnutls-dev libdbi0-dev libesmtp-dev libganglia1-dev libgcrypt11-dev libglib2.0-dev libhiredis-dev liblvm2-dev libmemcached-dev libmodbus-dev libmnl-dev libmysqlclient-dev libnotify-dev libopenipmi-dev liboping-dev libpcap0.8-dev  libpcap-dev libperl-dev libpq-dev libprotobuf-c0-dev librabbitmq-dev librrd-dev libsensors4-dev libsnmp-dev  libsnmp-dev  libsnmp9-dev libsnmp-dev  perl libtokyocabinet-dev libtokyotyrant-dev  libupsclient1-dev libvarnish-dev libvirt-dev libyajl-dev default-jdk protobuf-c-compiler python-dev
```

Building the package:
---------------------

* Fetch the [current version] and save it as `collectd_5.4.1-llnw6.orig.tar.gz`
  in the root of this repo
* Extract the source tree into 'collectd/':

    `tar xvzf collectd-5.4.1.llnw6.tar.gz -C collectd --strip-components=1`
* `cd collectd`
* `dpkg-buildpackage -us -uc`

Subtree maintenance:
--------------------

* `git subtree pull --prefix collectd git://git.tokkee.org/pkg-collectd master --squash` - merge or backout any conflicts
* `dch` - add a changelog entry and match the version to the new dist version

Ubuntu PPA:
-----------
* PPA: https://launchpad.net/~llnw/+archive/collectd

To perform a release, you need a launchpad.net account with an authorized GPG key.

* Alter collectd/debian/changelog for the release (i.e. append ~ubuntu14.04 to the version string, change release from unstable to trusty)
* `dpkg-buildpackage -S` - Create a source package for this Ubuntu version
* `dput ppa:llnw/collectd collectd_5.4.1-llnw6~ubuntu14.04_source.changes` - upload to launchpad.net build cluster


  [current version]: https://github.com/llnw/collectd/releases/download/collectd-5.4.1-llnw6/collectd-5.4.1.llnw6.tar.gz
