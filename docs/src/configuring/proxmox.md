# Proxmox Machinery

Proxmox is a virtualization platform that can be used to run Cuckoo's analysis VMs. This document describes how to configure the Proxmox machinery.

## Configuration

The Proxmox machinery is configured in `conf/machineries/proxmox.yaml`. The following options are available:

* `dsn`: The IP address or hostname of the Proxmox server.
* `user`: The username to connect to the Proxmox server.
* `pw`: The password for the user.
* `timeout`: The timeout for connecting to the Proxmox server.
* `verify_ssl`: Whether to verify the SSL certificate of the Proxmox server.
* `interface`: The network interface to use for the VMs.
* `machines`: A list of machines to use for analysis.

Each machine has the following options:

* `label`: The name of the VM in Proxmox.
* `ip`: The IP address of the VM.
* `platform`: The operating system of the VM.
* `os_version`: The version of the operating system.
* `architecture`: The architecture of the VM.
* `agent_port`: The port of the Cuckoo agent running in the VM.
* `mac_address`: The MAC address of the VM.
* `snapshot`: The name of the snapshot to use for analysis.
* `interface`: The network interface to use for the VM.
* `tags`: A list of tags to identify the VM.

## Example Configuration

```yaml
# Specify a IP-address for the proxmox server
# This module uses the std-port 8006 and as of now cant be changed.
dsn: "192.168.1.100"

# The User you want to use for connecting to proxmox
user: "root@pam"

# The corresponding password to the user
pw: "your-password"

# Timeout for establishing a connection
timeout: 10

# (Optional) Verify SSL connection to Proxmox server.
verify_ssl: True

# The Interface where the Analysis VMs also are
interface: eno1

machines:
  cuckoo1:
    label: cuckoo1
    ip: 192.168.1.101
    platform: windows
    os_version: "10"
    architecture: amd64
    agent_port: 8000
    snapshot: clean
    tags:
    - windows10
    - x64
```