---
layout: layout.pug
navigationTitle: dcos storage device
title: dcos storage device
menuWeight: 0
notes: Code generated by docgen.go, DO NOT EDIT
enterprise: true
beta: true
origin: github.com/mesosphere/dcos-storage/cli/pkg/cmd/cmd_device.go
---
## dcos storage device

Manage physical devices.

### Synopsis

There are typically storage devices that present as Linux devices on agents in
the cluster. The devices on a node can be assembled into volume providers that
expose their storage capacity to the rest of the cluster. For example, some
SSDs `xvdb` and `xvde` on node 2aada917-0ba0-4041-bb1e-4f16a57cd1a0-S0 can be
assembled into a LVM2 volume group on that node creating a new volume provider
and specifying the `plugin` as `lvm` and listing `xvdb` and `xvde` as the
devices.

```bash
dcos storage device [flags]
```

### Examples

1. Create the Devices volume provider on a node:

```bash
$ cat provider.json
{
    "name": "devices-provider",
    "description": "Expose devices on a node",
    "spec": {
        "plugin": "devices",
        "node": "ca626e4a-e3cb-4613-b7dd-618cfc19bee1-S0",
        "plugin-configuration": {
            "blacklist": "loop[0-9]"
        }
    }
}

$ dcos storage provider create provider.json
```

2. List all devices in the cluster:

```bash
$ dcos storage device list
NODE                                     NAME   STATUS  ROTATIONAL  TYPE  FSTYPE  MOUNTPOINT
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvda   ONLINE  false       disk  -       -
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvda1  ONLINE  false       part  xfs     /
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdb   ONLINE  false       disk  ext4    -
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvde   ONLINE  false       disk  xfs     /var/lib/mesos
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdf   ONLINE  false       disk  xfs     /var/lib/docker
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdg   ONLINE  false       disk  xfs     /dcos/volume0
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdh   ONLINE  false       disk  xfs     /var/log

$ dcos storage device list --json
{
    "devices": [
        {
            "name": "xvda",
            "status": {
                "state": "ONLINE",
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "metadata": {
                    "major": "202",
                    "minor": "0",
                    "name": "xvda",
                    "read-only": "false",
                    "removable": "false",
                    "rotational": "false",
                    "size": "161061273600",
                    "type": "disk"
                },
                "last-changed": "0001-01-01T00:00:00Z",
                "last-updated": "0001-01-01T00:00:00Z"
            }
        },
        {
            "name": "xvda1",
            "status": {
                "state": "ONLINE",
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "metadata": {
                    "fs-label": "root",
                    "fs-type": "xfs",
                    "fsuuid": "7f34470c-22e4-4c21-ad5d-64bc64b42ef3",
                    "major": "202",
                    "minor": "1",
                    "mount-point": "/",
                    "name": "xvda1",
                    "parent-name": "xvda",
                    "read-only": "false",
                    "removable": "false",
                    "rotational": "false",
                    "size": "161060208128",
                    "type": "part"
                },
                "last-changed": "0001-01-01T00:00:00Z",
                "last-updated": "0001-01-01T00:00:00Z"
            }
        },
        {
            "name": "xvdb",
            "status": {
                "state": "ONLINE",
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "metadata": {
                    "fs-label": "/mnt",
                    "fs-type": "ext4",
                    "fsuuid": "76dad0b0-f5d9-4408-8427-1a702676acea",
                    "major": "202",
                    "minor": "16",
                    "name": "xvdb",
                    "read-only": "false",
                    "removable": "false",
                    "rotational": "false",
                    "size": "161061273600",
                    "type": "disk"
                },
                "last-changed": "0001-01-01T00:00:00Z",
                "last-updated": "0001-01-01T00:00:00Z"
            }
        },
        {
            "name": "xvde",
            "status": {
                "state": "ONLINE",
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "metadata": {
                    "fs-type": "xfs",
                    "fsuuid": "b9e0cea3-9978-4cc7-a1df-0fe1440bde41",
                    "major": "202",
                    "minor": "64",
                    "mount-point": "/var/lib/mesos",
                    "name": "xvde",
                    "read-only": "false",
                    "removable": "false",
                    "rotational": "false",
                    "size": "53687091200",
                    "type": "disk"
                },
                "last-changed": "0001-01-01T00:00:00Z",
                "last-updated": "0001-01-01T00:00:00Z"
            }
        },
        {
            "name": "xvdf",
            "status": {
                "state": "ONLINE",
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "metadata": {
                    "fs-type": "xfs",
                    "fsuuid": "9fc123b8-2925-4d1b-b3db-a94363abae7d",
                    "major": "202",
                    "minor": "80",
                    "mount-point": "/var/lib/docker",
                    "name": "xvdf",
                    "read-only": "false",
                    "removable": "false",
                    "rotational": "false",
                    "size": "107374182400",
                    "type": "disk"
                },
                "last-changed": "0001-01-01T00:00:00Z",
                "last-updated": "0001-01-01T00:00:00Z"
            }
        },
        {
            "name": "xvdg",
            "status": {
                "state": "ONLINE",
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "metadata": {
                    "fs-type": "xfs",
                    "fsuuid": "eeeec093-3d2b-4bb9-96c0-efbddf6b61ab",
                    "major": "202",
                    "minor": "96",
                    "mount-point": "/dcos/volume0",
                    "name": "xvdg",
                    "read-only": "false",
                    "removable": "false",
                    "rotational": "false",
                    "size": "53687091200",
                    "type": "disk"
                },
                "last-changed": "0001-01-01T00:00:00Z",
                "last-updated": "0001-01-01T00:00:00Z"
            }
        },
        {
            "name": "xvdh",
            "status": {
                "state": "ONLINE",
                "node": "c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1",
                "metadata": {
                    "fs-type": "xfs",
                    "fsuuid": "2b9ee19c-3e51-4dd1-a769-329029afedf5",
                    "major": "202",
                    "minor": "112",
                    "mount-point": "/var/log",
                    "name": "xvdh",
                    "read-only": "false",
                    "removable": "false",
                    "rotational": "false",
                    "size": "21474836480",
                    "type": "disk"
                },
                "last-changed": "0001-01-01T00:00:00Z",
                "last-updated": "0001-01-01T00:00:00Z"
            }
        }
    ]
}
```

3. List all devices on a given node:

```bash
$ dcos node
HOSTNAME       IP           ID                                       TYPE               REGION      ZONE
10.10.0.39     10.10.0.39   c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  agent              us-west-2   us-west-2c
master.mesos.  10.10.0.139  c67efa5d-34fa-4bc5-8b21-2a5e0bd52385     master (leader)    us-west-2   us-west-2c

$ dcos storage device list --node c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1
NODE                                     NAME   STATUS  ROTATIONAL  TYPE  FSTYPE  MOUNTPOINT
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvda   ONLINE  false       disk  -       -
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvda1  ONLINE  false       part  xfs     /
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdb   ONLINE  false       disk  ext4    -
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvde   ONLINE  false       disk  xfs     /var/lib/mesos
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdf   ONLINE  false       disk  xfs     /var/lib/docker
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdg   ONLINE  false       disk  xfs     /dcos/volume0
c67efa5d-34fa-4bc5-8b21-2a5e0bd52385-S1  xvdh   ONLINE  false       disk  xfs     /var/log
```

### Options inherited from parent commands

```bash
  -h, --help               Help for this command.
  --timeout duration   Override the default request timeout. (default 55s)
```

### SEE ALSO

* [dcos storage](../)	 - Manage storage volumes, volume profiles and volume providers.
* [dcos storage device list](./dcos-storage-device-list/)	 - List physical devices.

