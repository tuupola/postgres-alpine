


With Alpine based image:

```
$ kubectl apply -k .
namespace/test created
statefulset.apps/postgres created

$ kubectl exec -it -n test statefulset/postgres -- bash
bash-5.1# df -h
Filesystem                Size      Used Available Use% Mounted on
overlay                 125.4G     33.0G     86.7G  28% /
tmpfs                    64.0M         0     64.0M   0% /dev
/dev/mapper/rl-root     125.4G     33.0G     86.7G  28% /etc/hosts
/dev/mapper/rl-root     125.4G     33.0G     86.7G  28% /dev/termination-log
/dev/mapper/rl-root     125.4G     33.0G     86.7G  28% /etc/hostname
/dev/mapper/rl-root     125.4G     33.0G     86.7G  28% /etc/resolv.conf
shm                      64.0M      1.0M     63.0M   2% /dev/shm
/dev/longhorn/pvc-7a73320e-4498-403a-a5ec-33d3c4f8ae76
                          7.8G     28.0K      7.8G   0% /var/lib/postgresql
/dev/mapper/rl-root     125.4G     33.0G     86.7G  28% /var/lib/postgresql/data
...
bash-5.1# exit
command terminated with exit code 1

$ kubectl delete -k .
namespace "test" deleted
statefulset.apps "postgres" deleted
```

With Debian based image:

```
$ kubectl apply -k .
namespace/test created
statefulset.apps/postgres created
$ kubectl exec -it -n test statefulset/postgres -- bash

bash-5.1# df -h
Filesystem                                              Size  Used Avail Use% Mounted on
overlay                                                 126G   34G   87G  28% /
tmpfs                                                    64M     0   64M   0% /dev
/dev/mapper/rl-root                                     126G   34G   87G  28% /etc/hosts
shm                                                      64M  1.1M   63M   2% /dev/shm
/dev/longhorn/pvc-7eab52f7-918e-4791-a924-74072998cd26  7.8G   28K  7.8G   1% /var/lib/postgresql
...
bash-5.1# exit
command terminated with exit code 1

$ kubectl delete -k .
namespace "test" deleted
statefulset.apps "postgres" deleted
```
