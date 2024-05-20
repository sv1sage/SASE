[Proxmox Virtual Environment]: https://www.proxmox.com/en/
[Axis Security]: https://www.axissecurity.com/schedule-a-demo/
[Axis Security Workspace]: https://auth.axissecurity.com/
[Linux Server - Ubuntu 22.04.4 LTS Jammy]: https://cloud-images.ubuntu.com/jammy/current/

# Use Case

User requires `ssh` access from an `unmanaged device` to an `internal hosted server`.

Requirements:
- Identify the user
- Single Sign-On experience
- Access policy based on least privilege
- Unmanaged device must not be placed onto the internal network

# ✅ Prerequisites

- [Axis Security Workspace]

- [Linux Server - Ubuntu 22.04.4 LTS Jammy]

# System Information

- Linux Server: Ubuntu 22.04.4 LTS Jammy

# ⚙️ Installation

## TASK 1: Linux Server Setup - SSH

### Update your package list:
```text
sudo apt update
```

### Install OpenSSH server:
```text
sudo apt install openssh-server
```

### Start SSH service:
```text
sudo systemctl start ssh
```

### Start SSH service at boot:
```text
sudo systemctl enable ssh
```

## OPTIONAL TASK 3: SSH authentication with rsa key
💡[Skip to Task 4](#task-4-create-a-ssh-application) if you want to use username and password authentication

### Change to user home direcotry && create `.ssh/` directory && change directory to `.ssh/`
```text
cd && mkdir .ssh/ && cd .ssh/
```
💡 if `.ssh/`directory is already present, just change directory
### 
```text
cd && cd .ssh/
```

### Create RSA keys
```text
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
💡
- leaving the passphrase empty will allow you to authenticate purely with your rsa key
- don't store an unprotected rsa key on file systems without strong protection

### Append the content of ìd_rsa.pub` to `authorized_keys`
```text
cat id_rsa.pub >> authorized_keys
```

### Set key permissions:
```text
chmod 600 id_rsa && chmod 644 id_rsa.pub
```

### Verify key permissions:
```text
ls -l
```

CLI output:
```text
-rw------- 1 your_username your_username 2223 May 20 06:41 authorized_keys
-rw------- 1 your_username your_username 3389 May 20 06:24 id_rsa
-rw-r--r-- 1 your_username your_username  748 May 20 06:24 id_rsa.pub
```

### Helpful information:
💡Increase security by updating your SSH configuration:
- Disable root login
```text
PermitRootLogin no
```
- Allow only specific users
```text
AllowUsers your_username
```
- Disable password authentication
```text
PasswordAuthentication yes
```

## TASK 4: Create a `ssh` application
