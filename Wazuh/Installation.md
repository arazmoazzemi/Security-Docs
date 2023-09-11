## Install Wazuh4.5.2 on kvm host



```bash
virt-install \
  --import --name wazuh \
  --memory 8192 \
  --vcpus 8 \
  --cpu host \
  --disk /var/lib/libvirt/images/wazuh-4.5.2.qcow2,format=qcow2,bus=virtio \
  --network bridge=virbr0,model=virtio \
  --osinfo detect=on,require=off \
  --noautoconsole  \
```
info
```
ssh root@<ip_address>
root
wazuh

http://localhost:80
user: admin
password: admin
```
Set static ip address:

```bash
nano /etc/sysconfig/network-scripts/ifcfg-eth0

TYPE=Ethernet
NAME=eth0
BOOTPROTO=none
IPADDR="192.168.122.88"
NETMASK="255.255.255.0"
GATEWAY=192.168.122.1
DNS1=8.8.8.8
DNS2=1.1.1.1
DEVICE=eth0
ONBOOT="yes"
PEERDNS=no


systemctl restart network
```

----

### [server agent remove](https://documentation.wazuh.com/current/user-manual/agents/remove-agents/remove.html)

Remove agent from server:
```bash
/var/ossec/bin/manage_agents

# Example:

/var/ossec/bin/manage_agents -r 001
```

Remove agent from windows host
```bash
msiexec.exe /x wazuh-agent-4.5.2-1.msi /qn
```
---
