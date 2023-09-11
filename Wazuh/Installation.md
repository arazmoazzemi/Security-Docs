## Install Wazuh on kvm host



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



----

### [server agent remove](https://documentation.wazuh.com/current/user-manual/agents/remove-agents/remove.html)

```bash
/var/ossec/bin/manage_agents

Example:

/var/ossec/bin/manage_agents -r 001
```
---
