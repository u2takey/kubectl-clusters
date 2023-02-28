# kubectl-cluster

Exec command on multiple clusters.


## Set cluster.ini 

Set cluster.ini in current dir or with Env `CLUSTER_CONFIG`

```
➜ cat clusters.ini
[test]
context=cls-test1 namespace=default
context=cls-test2

[prod]
context=cls-prod
```

clusters.ini is a `INI` like config, in which you can group clusters and set extra args for command.


## Exec 

```
# exec in all groups 
➜ kubectl clusters all get pod
[GROUP]: test --------------------------------------------------------------------------------
[CLUSTER]: cls-test1 --------------------------------------------------
[DEBUG] kubectl --context=cls-test1 --namespace=default get pod
NAME                                      READY   STATUS    RESTARTS   AGE
nginx-6dc5bfc797-vwdz7                    1/1     Running   0          32d


[GROUP]: prod --------------------------------------------------------------------------------
[CLUSTER]: cls-prod --------------------------------------------------
[DEBUG] kubectl --context=cls-qcvhpqog get pod
NAME                                READY   STATUS    RESTARTS   AGE
a4cgfxv7srbfhbsn-78479b5cf7-f85d8   2/2     Running   0          37d


# exec in single group
➜ kubectl clusters prod get pod
[GROUP]: prod --------------------------------------------------------------------------------
[CLUSTER]: cls-prod --------------------------------------------------
[DEBUG] kubectl --context=cls-qcvhpqog get pod
NAME                                READY   STATUS    RESTARTS   AGE
a4cgfxv7srbfhbsn-78479b5cf7-f85d8   2/2     Running   0          37d
```
