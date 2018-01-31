# Portal App Manager

This script helps an Agave tenant admin manage the contents of the [Discovery Workspace][1] in a TACC Portal app. Works with SD2E and [DesignSafe][2]. Only persons with admin-level access can manage the contents of the Discovery Workspace. 

## Usage

List the current visible catalog

```shell
$ portal-apps-manage get '*'
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| UUID                                  | Updated                       | AppId                 | Owner   | Type   | Public   |
+=======================================+===============================+=======================+=========+========+==========+
| 5480371260410892776-242ac11c-0001-012 | 2018-01-30T16:44:20.729-06:00 | fcs-etl-0.3.3u3       | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 742919250699742745-242ac11c-0001-012  | 2017-10-09T17:12:37.965-05:00 | kallisto-0.43.1u2     | sd2eadm | agave  | False    |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 3411571413273612776-242ac11c-0001-012 | 2018-01-30T16:30:33.346-06:00 | lcms-maverick-0.1.0u2 | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 5079135415618572776-242ac11c-0001-012 | 2018-01-30T16:31:12.171-06:00 | lcms-pyquant-0.1.0u1  | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 3809714881612812776-242ac11c-0001-012 | 2018-01-30T16:30:42.616-06:00 | lcms-wrangler-0.1.0u2 | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 4209705185889292776-242ac11c-0001-012 | 2018-01-30T16:30:51.928-06:00 | msf-maverick-0.1.0u1  | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 4542779899694092776-242ac11c-0001-012 | 2018-01-30T16:30:59.683-06:00 | msf-wrangler-0.1.0u1  | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 1515686949473292776-242ac11c-0001-012 | 2018-01-30T16:29:49.204-06:00 | rnaseq-0.1.2u1        | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
| 2251930243353612776-242ac11c-0001-012 | 2018-01-30T16:30:06.346-06:00 | rnaseq-broad-0.1.1u1  | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-----------------------+---------+--------+----------+
```

Find new Agave apps to publish

```shell
$ apps-list -P

apps-list -P
fcs-etl-0.3.3u3
rnaseq-0.1.2u1
ta3-api-0.0.2u1
lcms-pyquant-0.1.0u1
rnaseq-broad-0.1.1u1
rnaseq-0.1.1u1
sailfish-0.10.1u4
fcs-tasbe-0.2.0u6
lcms-maverick-0.1.0u2
lcms-wrangler-0.1.0u2
msf-maverick-0.1.0u1
msf-wrangler-0.1.0u1
sortmerna-0.0.1u1
hello-agave-hpc-0.1.0u1
hello-agave-cli-0.1.0u1
msf-0.1.0u3
kallisto-0.43.1u3
hello-container-0.1.0u1
```

Publish an app to Discovery Workspace

```shell
$ portal-apps-manage add hello-agave-cli-0.1.0u1
Trying to add hello-agave-cli-0.1.0u1...
Successfully added 8481275424206819816-242ac11c-0001-012
Successfully published 8481275424206819816-242ac11c-0001-012
```

Get the newly created entry

```shell
$ portal-apps-manage get hello-agave-cli-0.1.0u1
+---------------------------------------+-------------------------------+-------------------------+---------+--------+----------+
| UUID                                  | Updated                       | AppId                   | Owner   | Type   | Public   |
+=======================================+===============================+=========================+=========+========+==========+
| 8481275424206819816-242ac11c-0001-012 | 2018-01-30T17:58:25.345-06:00 | hello-agave-cli-0.1.0u1 | sd2eadm | agave  | True     |
+---------------------------------------+-------------------------------+-------------------------+---------+--------+----------+
```

Delete it from Discovery Workspace (but not the Agave app catalog)

```shell
$ portal-apps-manage del 8481275424206819816-242ac11c-0001-012
Successfully deleted 8481275424206819816-242ac11c-0001-012
```

[1]: https://sd2e.org/workspace/
[2]: https://www.designsafe-ci.org/rw/workspace/#/