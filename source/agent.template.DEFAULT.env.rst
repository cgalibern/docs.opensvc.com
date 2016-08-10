DEFAULT resource template
----

::


	##############################################################################
	#                                                                            #
	# DEFAULT                                                                    #
	#                                                                            #
	##############################################################################
	
	[DEFAULT]
	#
	# keyword:       mode
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      hosted
	#  candidates:   hosted | sg | vcs | rhcs
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The mode decides upon disposition OpenSVC takes to bring a service
	#         up or down : virtualized services need special actions to prepare
	#         and boot the container for example, which is not needed for 'hosted'
	#         services.
	#
	;mode = hosted
	
	#
	# keyword:       pkg_name
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      mode in ['vcs', 'sg', 'rhcs']
	#  scopable:     False
	#
	#  desc:  The wrapped cluster package name, as known to the cluster manager in
	#         charge.
	#
	;pkg_name = foo
	
	#
	# keyword:       docker_daemon_private
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      True
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  If set to False, this service will use the system's shared docker
	#         daemon instance. This is parameter is forced to False on non-Linux
	#         systems.
	#
	;docker_daemon_private = True
	
	#
	# keyword:       flex_primary
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      cluster_type in ['flex']
	#  scopable:     False
	#
	#  desc:  The node in charge of syncing the other nodes. --cluster actions on
	#         the flex_primary are execute on all peer nodes (ie, not drpnodes).
	#
	;flex_primary = foo
	
	#
	# keyword:       drp_flex_primary
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      cluster_type in ['flex']
	#  scopable:     False
	#
	#  desc:  The drpnode in charge of syncing the other drpnodes. --cluster
	#         actions on the drp_flex_primary are execute on all drpnodes (ie, not
	#         prd nodes).
	#
	;drp_flex_primary = foo
	
	#
	# keyword:       rollback
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      True
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  If set to False, the default rollback on action error is inhibited,
	#         leaving the service in its half-started state.
	#
	;rollback = True
	
	#
	# keyword:       status_schedule
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      @10
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The service status evaluation schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;status_schedule = @10
	
	#
	# keyword:       monitor_schedule
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      @1
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The service resource monitor schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;monitor_schedule = @1
	
	#
	# keyword:       push_schedule
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      00:00-06:00@361
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The service configuration emission to the collector schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;push_schedule = 00:00-06:00@361
	
	#
	# keyword:       docker_data_dir
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  If the service has docker-type container resources and
	#         docker_daemon_private is set to True, the service handles the
	#         startup of a private docker daemon. Its socket is
	#         <pathvar>/<svcname>/docker.sock, and its data directory must be
	#         specified using this parameter. This organization is necessary to
	#         enable service relocalization.
	#
	;docker_data_dir = /srv/svc1/data/docker
	
	#
	# keyword:       docker_daemon_args
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  If the service has docker-type container resources, the service
	#         handles the startup of a private docker daemon. OpenSVC sets the
	#         socket and data dir parameters. Admins can set extra parameters
	#         using this keyword. For example, it can be useful to set the --ip
	#         parameter for a docker registry service.
	#
	;docker_daemon_args = --ip 1.2.3.4
	
	#
	# keyword:       prkey
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  Defines a specific default persistent reservation key for the
	#         service. A prkey set in a resource takes priority. If no prkey is
	#         specified in the service nor in the DEFAULT section, the prkey in
	#         node.conf is used. If node.conf has no prkey set, the hostid is
	#         computed and written in node.conf.
	#
	;prkey = foo
	
	#
	# keyword:       anti_affinity
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  A whitespace separated list of services this service is not allowed
	#         to be started on the same node. The svcmgr --ignore-affinity option
	#         can be set to override this policy.
	#
	;anti_affinity = svc1 svc2
	
	#
	# keyword:       no_preempt_abort
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      False
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  If set to 'true', OpenSVC will preempt scsi reservation with a
	#         preempt command instead of a preempt and and abort. Some scsi target
	#         implementations do not support this last mode (esx). If set to
	#         'false' or not set, 'no_preempt_abort' can be activated on a per-
	#         resource basis.
	#
	;no_preempt_abort = False
	
	#
	# keyword:       show_disabled
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      True
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Specifies if the disabled resources must be included in the print
	#         status and json status output.
	#
	;show_disabled = True
	
	#
	# keyword:       cluster
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The symbolic name of the cluster. Used to label shared disks
	#         represented to tiers-2 consumers like containers.
	#
	;cluster = cluster1
	
	#
	# keyword:       cluster_type
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      failover
	#  candidates:   failover | flex | autoflex
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  failover: the service is allowed to be up on one node at a time.
	#         allactive: the service must be up on all nodes. flex: the service
	#         can be up on n out of m nodes (n <= m), n/m must be in the
	#         [flex_min_nodes, flex_max_nodes] range. autoflex: same as flex, but
	#         charge the collector to start the service on passive nodes when the
	#         average %cpu usage on active nodes > flex_cpu_high_threshold and
	#         stop the service on active nodes when the average %cpu usage on
	#         active nodes < flex_cpu_low_threshold.
	#
	;cluster_type = failover
	
	#
	# keyword:       service_type
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      PRD
	#  candidates:   PRD | PPRD | REC | INT | DEV | TST | TMP | DRP | FOR | PRA | PRJ | STG
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  A non-PRD service can not be brought up on a PRD node, but a PRD
	#         service can be startup on a non-PRD node (in a DRP situation).
	#
	;service_type = PRD
	
	#
	# keyword:       flex_min_nodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      1
	#  candidates:   None
	#  depends:      cluster_type in ['flex', 'autoflex']
	#  scopable:     False
	#
	#  desc:  Minimum number of active nodes in the cluster. Below this number
	#         alerts are raised by the collector, and the collector won't stop any
	#         more service instances.
	#
	;flex_min_nodes = 1
	
	#
	# keyword:       flex_max_nodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      10
	#  candidates:   None
	#  depends:      cluster_type in ['flex', 'autoflex']
	#  scopable:     False
	#
	#  desc:  Maximum number of active nodes in the cluster. Above this number
	#         alerts are raised by the collector, and the collector won't start
	#         any more service instances. 0 means unlimited.
	#
	;flex_max_nodes = 10
	
	#
	# keyword:       flex_cpu_min_threshold
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      10
	#  candidates:   None
	#  depends:      cluster_type in ['flex', 'autoflex']
	#  scopable:     False
	#
	#  desc:  Average CPU usage across the active cluster nodes below which the
	#         collector raises alerts and decides to stop service instances with
	#         autoflex cluster type.
	#
	;flex_cpu_min_threshold = 10
	
	#
	# keyword:       flex_cpu_max_threshold
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      70
	#  candidates:   None
	#  depends:      cluster_type in ['flex', 'autoflex']
	#  scopable:     False
	#
	#  desc:  Average CPU usage across the active cluster nodes above which the
	#         collector raises alerts and decides to start new service instances
	#         with autoflex cluster type.
	#
	;flex_cpu_max_threshold = 70
	
	#
	# keyword:       nodes
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      rhel71.opensvc.com
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  List of cluster local nodes able to start the service.  Whitespace
	#         separated.
	#
	;nodes = rhel71.opensvc.com
	
	#
	# keyword:       autostart_node
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      rhel71.opensvc.com
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  A whitespace-separated list subset of 'nodes'. Defines the nodes
	#         where the service will try to start on upon node reboot. On a
	#         failover cluster there should only be one autostart node and the
	#         start-up will fail if the service is already up on another node
	#         though. If not specified, the service will never be started at node
	#         boot-time, which is rarely the expected behaviour.
	#
	;autostart_node = rhel71.opensvc.com
	
	#
	# keyword:       drpnode
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The backup node where the service is activated in a DRP situation.
	#         This node is also a data synchronization target for 'sync'
	#         resources.
	#
	;drpnode = node1
	
	#
	# keyword:       nodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Alternate backup nodes, where the service could be activated in a
	#         DRP situation if the 'drpnode' is not available. These nodes are
	#         also data synchronization targets for 'sync' resources.
	#
	;nodes = node1 node2
	
	#
	# keyword:       encapnodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The list of containers handled by this service and with an OpenSVC
	#         agent installed to handle the encapsulated resources. With this
	#         parameter set, parameters can be scoped with the @encapnodes suffix.
	#
	;encapnodes = vm1 vm2
	
	#
	# keyword:       app
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      DEFAULT
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Used to identify who is responsible for is service, who is billable
	#         and provides a most useful filtering key. Better keep it a short
	#         code.
	#
	;app = DEFAULT
	
	#
	# keyword:       comment
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Helps users understand the role of the service, which is nice to on-
	#         call support people having to operate on a service they are not
	#         usualy responsible for.
	#
	;comment = foo
	
	#
	# keyword:       scsireserv
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      False
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  If set to 'true', OpenSVC will try to acquire a type-5 (write
	#         exclusive, registrant only) scsi3 persistent reservation on every
	#         path to disks of every disk group attached to this service. Existing
	#         reservations are preempted to not block service start-up. If the
	#         start-up was not legitimate the data are still protected from being
	#         written over from both nodes. If set to 'false' or not set,
	#         'scsireserv' can be activated on a per-resource basis.
	#
	;scsireserv = False
	
	#
	# keyword:       bwlimit
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Bandwidth limit in KB applied to all rsync transfers. Leave empty to
	#         enforce no limit.
	#
	;bwlimit = 3000
	
	#
	# keyword:       sync_interval
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      121
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Set the minimum delay between syncs in minutes. If a sync is
	#         triggered through crond or manually, it is skipped if last sync
	#         occured less than 'sync_min_delay' ago. The mecanism is enforced by
	#         a timestamp created upon each sync completion in
	#         <pathvar>/sync/[service]![dst]
	#
	;sync_interval = 121
	
	#
	# keyword:       sync_max_delay
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      1440
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Unit is minutes. This sets to delay above which the sync status of
	#         the resource is to be considered down. Should be set according to
	#         your application service level agreement. The cron job frequency
	#         should be set between 'sync_min_delay' and 'sync_max_delay'
	#
	;sync_max_delay = 1440
	
	#
	# keyword:       presnap_trigger
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Define a command to run before creating snapshots. This is most
	#         likely what you need to use plug a script to put you data in a
	#         coherent state (alter begin backup and the like).
	#
	;presnap_trigger = /srv/svc1/etc/init.d/pre_snap.sh
	
	#
	# keyword:       postsnap_trigger
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Define a command to run after snapshots are created. This is most
	#         likely what you need to use plug a script to undo the actions of
	#         'presnap_trigger'.
	#
	;postsnap_trigger = /srv/svc1/etc/init.d/post_snap.sh
	
	#
	# keyword:       monitor_action
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   reboot | crash | freezestop
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  The action to take when a monitored resource is not up nor standby
	#         up, and if the resource restart procedure has failed.
	#
	;monitor_action = reboot
	
	#
	# keyword:       create_pg
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      True
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Use process containers when possible. Containers allow capping
	#         memory, swap and cpu usage per service. Lxc containers are naturally
	#         containerized, so skip containerization of their startapp.
	#
	;create_pg = True
	
	#
	# keyword:       pg_cpus
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  Allow service process to bind only the specified cpus. Cpus are
	#         specified as list or range : 0,1,2 or 0-2
	#
	;pg_cpus = 0-2
	
	#
	# keyword:       pg_mems
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  Allow service process to bind only the specified memory nodes.
	#         Memory nodes are specified as list or range : 0,1,2 or 0-2
	#
	;pg_mems = 0-2
	
	#
	# keyword:       pg_cpu_shares
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  Kernel default value is used, which usually is 1024 shares. In a
	#         cpu-bound situation, ensure the service does not use more than its
	#         share of cpu ressource. The actual percentile depends on shares
	#         allowed to other services.
	#
	;pg_cpu_shares = 512
	
	#
	# keyword:       pg_cpu_quota
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  The percent ratio of one core to allocate to the process group if %
	#         is specified, else the absolute value to set in the process group
	#         parameter. For example, on Linux cgroups, -1 means unlimited, and a
	#         positive absolute value means the number of microseconds to allocate
	#         each period. 50%@all means 50% of all cores, and 50%@2 means 50% of
	#         two cores.
	#
	;pg_cpu_quota = 50%@all
	
	#
	# keyword:       pg_mem_oom_control
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  A flag (0 or 1) that enables or disables the Out of Memory killer
	#         for a cgroup. If enabled (0), tasks that attempt to consume more
	#         memory than they are allowed are immediately killed by the OOM
	#         killer. The OOM killer is enabled by default in every cgroup using
	#         the memory subsystem; to disable it, write 1.
	#
	;pg_mem_oom_control = 1
	
	#
	# keyword:       pg_mem_limit
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  Ensures the service does not use more than specified memory (in
	#         bytes). The Out-Of-Memory killer get triggered in case of
	#         tresspassing.
	#
	;pg_mem_limit = 512000000
	
	#
	# keyword:       pg_mem_swappiness
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  Set a swappiness value for the process group.
	#
	;pg_mem_swappiness = 40
	
	#
	# keyword:       pg_vmem_limit
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  Ensures the service does not use more than specified memory+swap (in
	#         bytes). The Out-Of-Memory killer get triggered in case of
	#         tresspassing. The specified value must be greater than pg_mem_limit.
	#
	;pg_vmem_limit = 1024000000
	
	#
	# keyword:       pg_blkio_weight
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      create_pg in [True]
	#  scopable:     False
	#
	#  desc:  Block IO relative weight. Value: between 10 and 1000. Kernel
	#         default: 1000.
	#
	;pg_blkio_weight = 50
	
	#
	# keyword:       disable
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      False
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A disabled resource will be ignored on service startup and shutdown.
	#
	;disable = False
	
