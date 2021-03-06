# cv4pve-diag

[![License](https://img.shields.io/github/license/Corsinvest/cv4pve-diag.svg)](LICENSE.md) [![AppVeyor branch](https://img.shields.io/appveyor/ci/franklupo/cv4pve-diag/master.svg)](https://ci.appveyor.com/project/franklupo/cv4pve-diag)

```text
    ______                _                      __
   / ____/___  __________(_)___ _   _____  _____/ /_
  / /   / __ \/ ___/ ___/ / __ \ | / / _ \/ ___/ __/
 / /___/ /_/ / /  (__  ) / / / / |/ /  __(__  ) /_
 \____/\____/_/  /____/_/_/ /_/|___/\___/____/\__/

Diagnostic for Proxmox VE         (Made in Italy)

Usage: cv4pve-diag [options]

Options:
  -?|-h|--help      Show help information
  --version         Show version information
  --host            The host name host[:port],host1[:port],host2[:port]
  --username        User name <username>@<realm>
  --password        The password. Specify 'file:path_file' to store password in file.
  --settings-file   File settings (generated from show-settings)  
  -o|--output       Type output (default: text) Text,Unicode,UnicodeAlt,Markdown,Html

Commands:
  app-check-update  Check update application
  app-upgrade       Upgrade application
  settings-create   Create file settings (settings.json)

Run 'cv4pve-diag [command] --help' for more information about a command.

cv4pve-diag is a part of suite cv4pve-tools.
For more information visit https://www.cv4pve-tools.com
```

## Copyright and License

Copyright: Corsinvest Srl
For licensing details please visit [LICENSE.md](LICENSE.md)

## Commercial Support

This software is part of a suite of tools called cv4pve-tools. If you want commercial support, visit the [site](https://www.cv4pve-tools.com)

## Introduction

Diagnostic for Proxmox VE.

this software collect data from Proxmox VE and output list of Warning/Critical/Info message.

## Main features

* Completely written in C#
* Use native api REST Proxmox VE (library C#)
* Independent os (Windows, Linux, Macosx)
* Installation unzip file extract binary
* Not require installation in Proxmox VE
* Execute out side Proxmox VE

## Configuration

E.g. install on linux 64

Download last package e.g. Debian cv4pve-diag-linux-x64.zip, on your os and install:

```sh
root@debian:~# unzip cv4pve-diag-linux-x64.zip
```

This tool need basically no configuration.

```sh
root@debian:~# cv4pve-diag --host=192.168.0.100 --username=root@pam --password=fagiano 
```

```sh
-------------------------------------------------------------------------------------------------------------------------------------
| Id                             | Description                                                  | Context | SubContext   | Gravity  |
-------------------------------------------------------------------------------------------------------------------------------------
| pve2                           | 1 Replication has errors                                     | Node    | Replication  | Critical |
| pve2                           | Zfs 'rpool' health problem                                   | Node    | Zfs          | Critical |
| qemu/312                       | Unknown resource qemu                                        | Qemu    | Status       | Critical |
| pve3                           | Node not online                                              | Node    | Status       | Warning  |
| local-zfs:vm-117-disk-1        | Image Orphaned                                               | Storage | Image        | Warning  |
| local-zfs:vm-105-disk-3        | Image Orphaned                                               | Storage | Image        | Warning  |
| qemu/121                       | Qemu Agent not enabled                                       | Qemu    | Agent        | Warning  |
| qemu/101                       | OS 'XP/2003' not mantained from vendor!                      | Qemu    | Agent        | Warning  |
| qemu/101                       | Qemu Agent not enabled                                       | Qemu    | Agent        | Warning  |
| 103                            | cv4pve-autosnap not configured                               | Qemu    | AutoSnapshot | Warning  |
| 115                            | vzdump backup not configured                                 | Qemu    | Backup       | Warning  |
| 205                            | vzdump backup not configured                                 | Qemu    | Backup       | Warning  |
| 103                            | vzdump backup not configured                                 | Qemu    | Backup       | Warning  |
| 313                            | vzdump backup not configured                                 | Qemu    | Backup       | Warning  |
| qemu/117                       | Unused disk0                                                 | Qemu    | Hardware     | Warning  |
| qemu/115                       | Cdrom mounted                                                | Qemu    | Hardware     | Warning  |
| 121                            | 10 snapshots older than 1 month                              | Qemu    | Snapshot     | Warning  |
| 313                            | 10 snapshots older than 1 month                              | Qemu    | Snapshot     | Warning  |
| qemu/500                       | Start on boot not enabled                                    | Qemu    | StartOnBoot  | Warning  |
| qemu/117                       | Start on boot not enabled                                    | Qemu    | StartOnBoot  | Warning  |
| 114                            | 10 snapshots older than 1 month                              | Lxc     | Snapshot     | Warning  |
| pve1                           | 3 Update availble                                            | Node    | Update       | Info     |
| pve2                           | 6 Update availble                                            | Node    | Update       | Info     |
| qemu/109                       | For more performance switch 'scsi0' hdd to VirtIO            | Qemu    | VirtIO       | Info     |
-------------------------------------------------------------------------------------------------------------------------------------
```

For change settings create file using settings-create command. Edit file and execute new settings using parameter --settings-file.
