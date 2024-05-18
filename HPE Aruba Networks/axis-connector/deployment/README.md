[Promox Virtual Environment]: https://www.proxmox.com/en/
[Axis Security]: https://www.axissecurity.com/schedule-a-demo/
[Axis Security Workspace]: https://auth.axissecurity.com/

# ✅ Prerequisites

- [Axis Securtiy Workspace]

- [Promox Virtual Environment]

# Overview

Deploy Atmos Connector on Proxmox Virtual Environment
- Atmos Connector Version: 3.51.1
- Proxmox Virtual Environment Version: 8.2.2

# 🚀 Installation

## TASK 1: Connect to the Management System of Axis Security:

```text
https://auth.axissecurity.com/
```

## TASK 2: Create Connector:
`settings` ➡️ `connectors` ➡️ `New Connector`

Step 1:

![Step 1](./images/new-connector-1.png)

Step 2:

![Step 2](./images/new-connector-2.png)

Step 3:

![Step 3](./images/new-connector-3.png)

Step 4:

![Step 4](./images/new-connector-4.png)

❗ right-click on `Download OVA` and copy link address and save it to a text editor of your choice❗

Step 5:

![Step 5](./images/new-connector-5.png)

❗ copy and save the one-time code generated to a text editor of your choice, one-time code is required for the initial activation ❗

## TASK 3: SSH to your Proxmox Virtual Environment instance with `root`:

Change directory to `root`:
```text
cd /root
```
Create directory `ova-import`:
```text
mkdir ova-import
```

Change directory to `ova-import`:
```text
cd ova-import/
```

Download Atmos Connector OVA:
```text
wget https://download.axissecurity.com/ova/axis-connector-ova-rocky-linux/axis-connector-rocky-linux-9-nci.ova
```

Extract Atmos Connector OVA:
```text
tar xvf axis-connector-rocky-linux-9-nci.ova 
```

Create a virtual machine based on the file with the extension `.ovf`:
```text
qm importovf 999 axis-connector-rocky-linux-9-nci-docker-v3.51.1.ovf local-lvm  --format qcow2
```

Attach the Atmos Connector disk to the new VM:
```text
qm importdisk 999 axis-connector-rocky-linux-9-nci-docker-v3.51.1-disk1.vmdk local-lvm --format qcow2
```


⚙️ 🔥 🔨 