# docker-server-coreos

## Default Setting
- Network
  - local only
  - private IP: 192.168.33.101
- Synced Folder
  - local_dir: ../../share
  - server_dir: /home/core/share
- Vagrant API vesion v2
- docker-compose version : v1.12.0

## Get started

```
$ git clone https://github.com/oshou/docker-server-coreos.git
$ cd docker-server-coreos
$ vagrant up
```

## Notice
- CoreOS is minimal & very fast. But...
  - no package management system(yum, apt...)
  - read-only file system(you can't edit /usr or /etc file)
