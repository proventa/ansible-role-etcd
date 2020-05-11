[![Build Status](https://travis-ci.com/yanehi/ansible-role-etcd.svg?branch=master)](https://travis-ci.org/yanehi/ansible-role-etcd)
# ansible-role-etcd
Role for deploying an high-available etcd cluster (key-value-store) on CentOS7. [Kubernetes](https://github.com/kubernetes/kubernetes) (save cluster state) or [Patroni](https://github.com/zalando/patroni) (postgres ha leader election) from [Zalando]() use this in their backend.


## Requirements

No special requirements; note that this role requires root access.

## Deploy the role

* add etcd-servers (because of raft protocol 3,5 or 7) to your `/etc/ansible/hosts`
* test the connection form ansible host to your etcd-servers

```bash
ansible -m ping etcd-servers
```

* rollout your playbook

```bash
git clone https://github.com/yanehi/ansible-role-etcd.git
ansible-playbook ansible-role-etcd/site.yml
```

## etcdctl

* get the leader of the cluster

```bash
etcdctl -w table --endpoints=etcd1:2379,etcd2:2379,etcd0:2379 endpoint status
```
## License

MIT

## Author Information

This role was created in 2020 by Yannic Nevado.