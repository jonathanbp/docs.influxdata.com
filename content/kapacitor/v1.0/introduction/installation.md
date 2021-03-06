---
title: Installation

menu:
  kapacitor_1_0:
    weight: 10
    parent: introduction
---

This page provides directions for installing, starting, and configuring Kapacitor.

## Requirements

For packaged installations, root or sudo access may be required to
complete the installation.

### Networking

Kapacitor listens on TCP port `9092` for all API and write
calls. 

Kapacitor may also bind to randomized UDP ports
for handling of InfluxDB data via subscriptions.

## Installation

Kapacitor has two binaries:

* kapacitor -- a CLI program for calling the Kapacitor API.
* kapacitord -- the Kapacitor server daemon.

You can either download the binaries directly from the
[downloads](https://influxdata.com/downloads/#kapacitor) page or by
using the Go command `go get`:

```bash
go get github.com/influxdb/kapacitor/cmd/kapacitor
go get github.com/influxdb/kapacitor/cmd/kapacitord
```

### Start the Kapacitor Service

For packaged installations, please see the respective sections below
for your operating system. For non-packaged installations (tarballs or
from source), you will need to start the Kapacitor application
manually by running:

```
./kapacitord -config <PATH TO CONFIGURATION>
```

#### OS X (via Homebrew)

To have `launchd` start Kapacitor at login:

```
ln -sfv /usr/local/opt/kapacitor/*.plist ~/Library/LaunchAgents
```

Then to load Kapacitor now:

```
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.kapacitor.plist
```

Or, if you don't want/need `lanchctl`, you can just run:

```
kapacitord -config /usr/local/etc/kapacitor.conf
```

#### Linux - SysV or Upstart Systems

To start the Kapacitor service, run:

```
sudo service kapacitor start
```

#### Linux - systemd Systems

To start the Kapacitor service, run:

```
sudo systemctl start kapacitor
```

## Configuration

An example configuration file can be found [here](https://github.com/influxdb/kapacitor/blob/master/etc/kapacitor/kapacitor.conf)

Kapacitor can also provide an example config for you using this command:

```bash
kapacitord config
```

To generate a new configuration file, run:
```
kapacitord config > kapacitor.generated.conf
```
