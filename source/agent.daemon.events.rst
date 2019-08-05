Daemon Events
=============

Id ``blacklist_add``
--------------------

sender {sender} blacklisted

Id ``hb_stale``
---------------

node {nodename} hb status beating => stale

Id ``max_stdby_resource_restart``
---------------------------------

max restart ({restart}) reached for standby resource {rid} ({resource.label})

Id ``resource_degraded``
------------------------

resource {rid} ({resource.label}) degraded to {resource.status} {resource.log}

Id ``resource_restart``
-----------------------

restart resource {rid} ({resource.label}) {resource.status} {resource.log}, try {try}/{restart}

Id ``arbitrator_up``
--------------------

arbitrator {arbitrator} is now reachable

Id ``monitor_started``
----------------------

monitor started

Id ``scale_up``
---------------

misses {delta} instance to reach scale target {instance.scale}

Id ``scale_down``
-----------------

exceeds {delta} instance to reach scale target {instance.scale}

Id ``service_config_installed``
-------------------------------

config fetched from node {from} is now installed

Id ``stdby_resource_restart``
-----------------------------

start standby resource {rid} ({resource.label}) {resource.status} {resource.log}, try {try}/{restart}

Id ``arbitrator_down``
----------------------

arbitrator {arbitrator} is no longer reachable

Id ``max_resource_restart``
---------------------------

max restart ({restart}) reached for resource {rid} ({resource.label})

Id ``node_thaw``
----------------

thaw node

Id ``node_config_change``
-------------------------

node config change

Id ``hb_beating``
-----------------

node {nodename} hb status stale => beating

Id ``resource_toc``
-------------------

toc for resource {rid} ({resource.label}) {resource.status} {resource.log}

Id ``crash``, Reason ``split``
------------------------------

cluster is split, we don't have quorum: {node_votes}+{arbitrator_votes}/{voting} votes {pro_voters}

Id ``forget_peer``, Reason ``no_rx``
------------------------------------

no rx thread still receive from node {peer} and maintenance grace period expired. flush its data

Id ``instance_abort``, Reason ``target``
----------------------------------------

abort {instance.topology} {instance.avail} instance {instance.monitor.local_expect} action to satisfy the {instance.monitor.global_expect} target

Id ``instance_delete``, Reason ``target``
-----------------------------------------

delete {instance.topology} {instance.avail} instance to satisfy the {instance.monitor.global_expect} target

Id ``instance_freeze``, Reason ``install``
------------------------------------------

freeze instance on install

Id ``instance_freeze``, Reason ``merge_frozen``
-----------------------------------------------

freeze instance on rejoin because instance on {peer} is frozen

Id ``instance_freeze``, Reason ``target``
-----------------------------------------

freeze instance to satisfy the {instance.monitor.global_expect} target

Id ``instance_provision``, Reason ``target``
--------------------------------------------

provision {instance.topology} {instance.avail} instance to satisfy the {instance.monitor.global_expect} target

Id ``instance_purge``, Reason ``target``
----------------------------------------

purge {instance.topology} {instance.avail} instance to satisfy the {instance.monitor.global_expect} target

Id ``instance_start``, Reason ``from_ready``
--------------------------------------------

start {instance.topology} {instance.avail} instance ready for {since} seconds

Id ``instance_start``, Reason ``single_node``
---------------------------------------------

start idle single node {instance.avail} instance

Id ``instance_start``, Reason ``target``
----------------------------------------

start {instance.topology} {instance.avail} instance to satisfy the {instance.monitor.global_expect} target

Id ``instance_stop``, Reason ``flex_threshold``
-----------------------------------------------

stop {instance.topology} {instance.avail} instance to meet threshold constraints: {up}/{instance.flex_target}

Id ``instance_stop``, Reason ``target``
---------------------------------------

stop {instance.topology} {instance.avail} instance to satisfy the {instance.monitor.global_expect} target

Id ``instance_thaw``, Reason ``target``
---------------------------------------

thaw instance to satisfy the {instance.monitor.global_expect} target

Id ``instance_unprovision``, Reason ``target``
----------------------------------------------

unprovision {instance.topology} {instance.avail} instance to satisfy the {instance.monitor.global_expect} target

Id ``node_freeze``, Reason ``kern_freeze``
------------------------------------------

freeze node due to kernel cmdline flag.

Id ``node_freeze``, Reason ``merge_frozen``
-------------------------------------------

freeze node, node {peer} was frozen while we were down

Id ``node_freeze``, Reason ``rejoin_expire``
--------------------------------------------

freeze node, the cluster is not complete on rejoin grace period expiration

Id ``node_freeze``, Reason ``target``
-------------------------------------

freeze node

Id ``node_freeze``, Reason ``upgrade``
--------------------------------------

freeze node for upgrade until the cluster is complete

Id ``node_thaw``, Reason ``upgrade``
------------------------------------

thaw node after upgrade, the cluster is complete

Id ``resource_would_toc``, Reason ``no_candidate``
--------------------------------------------------

would toc for resource {rid} ({resource.label}) {resource.status} {resource.log}, but no node is candidate for takeover.

