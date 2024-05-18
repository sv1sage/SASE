[Promox Virtual Environment]: https://www.proxmox.com/en/
[Axis Security]: https://www.axissecurity.com/schedule-a-demo/
[Axis Security Workspace]: https://auth.axissecurity.com/

# ✅ Prerequisites

- [Axis Security Workspace]

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

❗right-click on `Download OVA` and copy link address and save it to a text editor of your choice❗

Step 5:

![Step 5](./images/new-connector-5.png)

❗click on `copy` and save the one-time code generated to a text editor of your choice, one-time code is required for the initial activation❗

## TASK 3: Create a Virtual Machine for the Atmos Connector on Proxmox Virtual Environment:

`ssh`as `root` to your Proxmox Virtual Environment instance and run following commands:

### Change directory to `root`:
```text
cd /root
```

### Create directory `ova-import`:
```text
mkdir ova-import
```

### Change directory to `ova-import`:
```text
cd ova-import/
```

### Download Atmos Connector OVA:
```text
wget https://download.axissecurity.com/ova/axis-connector-ova-rocky-linux/axis-connector-rocky-linux-9-nci.ova
```

### Extract Atmos Connector OVA:
```text
tar xvf axis-connector-rocky-linux-9-nci.ova 
```

### Create a virtual machine based on the file with the extension `.ovf`:
```text
qm importovf 999 axis-connector-rocky-linux-9-nci-docker-v3.51.1.ovf local-lvm  --format qcow2
```
💡Note: 
- `999`is the VM ID feel free to change the value.
- `local-lvm`is the default storage ID, change the value to match your setup.

🔨 Following `warning`messages can be ignored:
```text
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_CTYPE = "UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
warning: unable to parse the VM name in this OVF manifest, generating a default value
invalid host ressource /disk/vmdisk1, skipping
```

### Attach the Atmos Connector disk to the new VM:
```text
qm importdisk 999 axis-connector-rocky-linux-9-nci-docker-v3.51.1-disk1.vmdk local-lvm --format qcow2
```
💡Note: if you changed the VM or storage ID, change the values to match your setup.

### Switch to the Graphical User Interface of your Proxmox Virtual Environment instance and complete the virtual machine setup:

Select the VM and follow these steps:

![Step 1](./images/gui-vm-settings-1.png)

Step 2:

![Step 2](./images/gui-vm-settings-2.png)

Step 3:

![Step 3](./images/gui-vm-settings-3.png)

Step 4:

![Step 4](./images/gui-vm-settings-4.png)

Step 5:

![Step 5](./images/gui-vm-settings-5.png)

Step 6:

![Step 6](./images/gui-vm-settings-6.png)

Step 7:

![Step 7](./images/gui-vm-settings-7.png)

Step 8:

![Step 8](./images/gui-vm-settings-8.png)

Step 9:

![Step 9](./images/gui-vm-settings-9.png)

## TASK 4: Deploy the Atmos Connector on Proxmox Virtual Environment:



⚙️ 🔥 🔨 