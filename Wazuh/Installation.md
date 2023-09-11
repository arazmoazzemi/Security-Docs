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


----

### [server agent remove](https://documentation.wazuh.com/current/user-manual/agents/remove-agents/remove.html)

```bash
/var/ossec/bin/manage_agents

# Example:

/var/ossec/bin/manage_agents -r 001
```
---
