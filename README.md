# debian-mariadb-10.0

This repository provides mariadb-10.0 debianized source package for Debian Stretch.

Source repository - https://github.com/MariaDB/server/tree/10.0

## Install build requirements:

```sh
apt-get -qq update && apt-get install build-essential bison chrpath debhelper devscripts dh-apparmor dh-exec dpatch fakeroot gawk gdb git libboost-dev libjemalloc-dev libjudy-dev libncurses5-dev libpam0g-dev libssl1.0-dev libwrap0-dev lsb-release po-debconf zlib1g-dev cmake libaio-dev libreadline-gplv2-dev
```

## Clone this branch to your build server:

```sh
cd /root
git clone https://github.com/kautMaks/debian-mariadb-10.0.git
```

## Get mariadb-10.0.38 sources:

```sh
wget https://downloads.mariadb.org/interstitial/mariadb-10.0.38/source/mariadb-10.0.38.tar.gz
tar --exclude='mariadb-10.0.38/debian' -xvf mariadb-10.0.38.tar.gz && mv mariadb-10.0.38/* debian-mariadb-10.0/ && rm -r mariadb-10.0.38
cd  debian-mariadb-10.0
```

## Build mariadb with disabled tests (recommended):
Don't run the mysql-test-run test suite as part of build. It takes a lot of time, and we will do a better test anyway in Buildbot, running the test suite from installed .debs on a clean VM.

```
DEB_BUILD_OPTIONS=nocheck debuild -us -uc -b
```

## Build mariadb with enabled tests (not recommended, takes a lot of time):

```
debuild -us -uc -b
```
