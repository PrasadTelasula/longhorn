Steps:
1. create Kubernetes Cluster with 3 worker nodes.

```
root@ip-172-31-8-35:~# kubectl get nodes
NAME               STATUS   ROLES    AGE   VERSION
ip-172-31-10-206   Ready    <none>   90m   v1.18.2+k3s1
ip-172-31-9-86     Ready    <none>   90m   v1.18.2+k3s1
ip-172-31-13-158   Ready    <none>   90m   v1.18.2+k3s1
ip-172-31-8-35     Ready    master   94m   v1.18.2+k3s1
root@ip-172-31-8-35:~#
```

2. Attach additional disks to all worker nodes (at lease 50 GB ).

```
root@ip-172-31-9-86:~# lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0     7:0    0 93.8M  1 loop /snap/core/8935
loop1     7:1    0   18M  1 loop /snap/amazon-ssm-agent/1566
xvda    202:0    0   20G  0 disk
└─xvda1 202:1    0   20G  0 part /
xvdb    202:16   0   50G  0 disk
```

3. Format and Mount the disks at /var/lib/longhorn on all worker nodes.
# lsblk
# sudo mkfs -t xfs /dev/xvdb
# sudo mkdir /var/lib/longhorn
# sudo mount /dev/xvdb /var/lib/longhorn
