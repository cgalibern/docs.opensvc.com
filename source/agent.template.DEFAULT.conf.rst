DEFAULT resource template
-------------------------

::

	##############################################################################
	#                                                                            #
	# DEFAULT                                                                    #
	#                                                                            #
	##############################################################################
	
	[DEFAULT]
	#
	# keyword:          mode
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         hosted
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      hosted
	#
	#  desc:  Deprecated. The value is always 'hosted'. The keyword is kept around
	#         for now the ease transition from older agents.
	#
	;mode = hosted
	
	#
	# keyword:          lock_timeout
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         60
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         duration
	#
	#  desc:  A duration expression, like '1m30s'. The maximum wait time for the
	#         action lock acquire. The svcmgr --waitlock option overrides this
	#         parameter.
	#
	;lock_timeout = 60
	
	#
	# keyword:          docker_daemon_private
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         True
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         boolean
	#
	#  desc:  If set to False, this service will use the system's shared docker
	#         daemon instance. This is parameter is forced to False on non-Linux
	#         systems.
	#
	;docker_daemon_private = True
	
	#
	# keyword:          flex_primary
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         <first node of the nodes parameter>
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         cluster_type in ['flex']
	#
	#  desc:  The node in charge of syncing the other nodes. --cluster actions on
	#         the flex_primary are execute on all peer nodes (ie, not drpnodes).
	#
	;flex_primary = <first node of the nodes parameter>
	
	#
	# keyword:          drp_flex_primary
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         <first node of the drpnodes parameter>
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         cluster_type in ['flex']
	#
	#  desc:  The drpnode in charge of syncing the other drpnodes. --cluster
	#         actions on the drp_flex_primary are execute on all drpnodes (ie, not
	#         pri nodes).
	#
	;drp_flex_primary = <first node of the drpnodes parameter>
	
	#
	# keyword:          rollback
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         True
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         boolean
	#
	#  desc:  If set to False, the default rollback on action error is inhibited,
	#         leaving the service in its half-started state.
	#
	;rollback = True
	
	#
	# keyword:          status_schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         @10
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The service status evaluation schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;status_schedule = @10
	
	#
	# keyword:          comp_schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         00:00-06:00@361
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The service compliance run schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;comp_schedule = 00:00-06:00@361
	
	#
	# keyword:          monitor_schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         @1
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The service resource monitor schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;monitor_schedule = @1
	
	#
	# keyword:          resinfo_schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         @60
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The service resource info push schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;resinfo_schedule = @60
	
	#
	# keyword:          push_schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         00:00-06:00@361
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The service configuration emission to the collector schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;push_schedule = 00:00-06:00@361
	
	#
	# keyword:          sync_schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         04:00-06:00@121
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The default sync resources schedule. See
	#         usr/share/doc/template.node.conf for the schedule syntax.
	#
	;sync_schedule = 04:00-06:00@121
	
	#
	# keyword:          aws
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The aws cli executable fullpath. If not provided, aws is expected to
	#         be found in the PATH.
	#
	;aws = foo
	
	#
	# keyword:          aws_profile
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         default
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The profile to use with the AWS api.
	#
	;aws_profile = default
	
	#
	# keyword:          docker_exe
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  If you have multiple docker versions installed and want the service
	#         to stick to a version whatever the PATH definition, you should set
	#         this parameter to the full path to the docker executable.
	#
	;docker_exe = /usr/bin/docker-1.8
	
	#
	# keyword:          dockerd_exe
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  If you have multiple docker versions installed and want the service
	#         to stick to a version whatever the PATH definition, you should set
	#         this parameter to the full path to the docker daemon executable.
	#
	;dockerd_exe = /usr/bin/dockerd-1.8
	
	#
	# keyword:          docker_data_dir
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
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
	# keyword:          docker_daemon_args
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  If the service has docker-type container resources, the service
	#         handles the startup of a private docker daemon. OpenSVC sets the
	#         socket and data dir parameters. Admins can set extra parameters
	#         using this keyword. For example, it can be useful to set the --ip
	#         parameter for a docker registry service.
	#
	;docker_daemon_args = --ip 1.2.3.4
	
	#
	# keyword:          docker_swarm_args
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The arguments passed to docker swarm init on the flex primary, and
	#         to docker swarm join on the the other nodes. The --token argument
	#         must not be specified, as it is handled by the agent. Scoping this
	#         parameter permits to set additional parameters on the flex_primary
	#         for use with swarm init only, like --autolock.
	#
	;docker_swarm_args = --advertize-addr {ip#0.ipname} --listen-addr {ip#0.ipname}
	
	#
	# keyword:          prkey
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Defines a specific default persistent reservation key for the
	#         service. A prkey set in a resource takes priority. If no prkey is
	#         specified in the service nor in the DEFAULT section, the prkey in
	#         node.conf is used. If node.conf has no prkey set, the hostid is
	#         computed and written in node.conf.
	#
	;prkey = foo
	
	#
	# keyword:          hard_affinity
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         set([])
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         set
	#
	#  desc:  A whitespace separated list of services that must be started on the
	#         node to allow the monitor to start this service.
	#
	;hard_affinity = set([])
	
	#
	# keyword:          hard_anti_affinity
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         set([])
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         set
	#
	#  desc:  A whitespace separated list of services that must not be started on
	#         the node to allow the monitor to start this service.
	#
	;hard_anti_affinity = set([])
	
	#
	# keyword:          soft_affinity
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         set([])
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         set
	#
	#  desc:  A whitespace separated list of services that must be started on the
	#         node to allow the monitor to start this service. If the local node
	#         is the only candidate ignore this constraint and allow start.
	#
	;soft_affinity = set([])
	
	#
	# keyword:          soft_anti_affinity
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         set([])
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         set
	#
	#  desc:  A whitespace separated list of services that must not be started on
	#         the node to allow the monitor to start this service. If the local
	#         node is the only candidate ignore this constraint and allow start.
	#
	;soft_anti_affinity = set([])
	
	#
	# keyword:          show_disabled
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         True
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  Specifies if the disabled resources must be included in the print
	#         status and json status output.
	#
	;show_disabled = True
	
	#
	# keyword:          cluster
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The symbolic name of the cluster. Used to label shared disks
	#         represented to tiers-2 consumers like containers.
	#
	;cluster = cluster1
	
	#
	# keyword:          cluster_type
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         failover
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      failover | flex
	#
	#  desc:  failover: the service is allowed to be up on one node at a time.
	#         allactive: the service must be up on all nodes. flex: the service
	#         can be up on n out of m nodes (n <= m), n/m must be in the
	#         [flex_min_nodes, flex_max_nodes] range.
	#
	;cluster_type = failover
	
	#
	# keyword:          env
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         <same as node env>
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      DEV | DRP | FOR | INT | PRA | PRD | PRJ | PPRD | REC | STG | TMP | TST | UAT
	#
	#  desc:  A non-PRD service can not be brought up on a PRD node, but a PRD
	#         service can be startup on a non-PRD node (in a DRP situation). The
	#         default value is the node env.
	#
	;env = <same as node env>
	
	#
	# keyword:          no_preempt_abort
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         False
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  If set to 'true', OpenSVC will preempt scsi reservation with a
	#         preempt command instead of a preempt and and abort. Some scsi target
	#         implementations do not support this last mode (esx). If set to
	#         'false' or not set, 'no_preempt_abort' can be activated on a per-
	#         resource basis.
	#
	;no_preempt_abort = False
	
	#
	# keyword:          orchestrate
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         ha
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      ha | start | no
	#  convert:         string
	#
	#  desc:  If set to 'no', disable service orchestration by the OpenSVC daemon
	#         monitor, including service start on boot. If set to 'start' failover
	#         services won't failover automatically, though the service instance
	#         on the natural placement leader is started if another instance is
	#         not already up. Flex services won't start missing instances to meet
	#         the flex_min_nodes target, though the <flex_min_nodes>th instances
	#         on best placement leaders are started if the instances minimum quota
	#         is not already reached. Resource restart is still active whatever
	#         the orchestrate value.
	#
	;orchestrate = ha
	
	#
	# keyword:          placement
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         nodes order
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      nodes order | load avg
	#
	#  desc:  Set a service instances placement policy. nodes order: the left-most
	#         available node is allowed to start a service instance when
	#         necessary. load avg: the least loaded node.
	#
	;placement = nodes order
	
	#
	# keyword:          constraints
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         orchestrate in ha
	#
	#  desc:  An expression evaluating as a boolean, constraining the service
	#         instance placement by the daemon monitor to nodes with the
	#         constraints evaluated as True. The constraints are not honored by
	#         manual start operations. The constraints value is embedded in the
	#         json status. Supported comparison operators are '==', '!=', '>',
	#         '>=', '<=', 'in (e1, e2)', 'in [e1, e2]'. Supported arithmetic
	#         operators are '*', '+', '-', '/', '**', '//', '%'. Supported binary
	#         operators are '&', '|', '^'. The negation operator is 'not'.
	#         Supported boolean operators are 'and', 'or'. References are allowed.
	#         Strings, and references evaluating as strings, containing dots must
	#         be quoted.
	#
	;constraints = $("{nodename}"=="n2.opensvc.com")
	
	#
	# keyword:          flex_min_nodes
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         1
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         cluster_type in ['flex']
	#  convert:         integer
	#
	#  desc:  Minimum number of active nodes in the cluster. Below this number
	#         alerts are raised by the collector, and the collector won't stop any
	#         more service instances.
	#
	;flex_min_nodes = 1
	
	#
	# keyword:          flex_max_nodes
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         10
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         cluster_type in ['flex']
	#  convert:         integer
	#
	#  desc:  Maximum number of active nodes in the cluster. Above this number
	#         alerts are raised by the collector, and the collector won't start
	#         any more service instances. 0 means unlimited.
	#
	;flex_max_nodes = 10
	
	#
	# keyword:          flex_cpu_low_threshold
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         10
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         cluster_type in ['flex']
	#  convert:         integer
	#
	#  desc:  Cluster-wide load average below which flex service instances will be
	#         stopped.
	#
	;flex_cpu_low_threshold = 10
	
	#
	# keyword:          flex_cpu_high_threshold
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         70
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         cluster_type in ['flex']
	#  convert:         integer
	#
	#  desc:  Cluster-wide load average above which flex new service instances
	#         will be started.
	#
	;flex_cpu_high_threshold = 70
	
	#
	# keyword:          docker_swarm_managers
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  List of nodes promoted as docker swarm managers.The flex primary
	#         node is implicitely a manager. Whitespace separated.
	#
	;docker_swarm_managers = foo
	
	#
	# keyword:          nodes
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         <hostname of the current node>
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         list_lower
	#
	#  desc:  List of cluster local nodes able to start the service.  Whitespace
	#         separated.
	#
	;nodes = <hostname of the current node>
	
	#
	# keyword:          drpnode
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The backup node where the service is activated in a DRP situation.
	#         This node is also a data synchronization target for 'sync'
	#         resources.
	#
	;drpnode = node1
	
	#
	# keyword:          drpnodes
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         []
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         list_lower
	#
	#  desc:  Alternate backup nodes, where the service could be activated in a
	#         DRP situation if the 'drpnode' is not available. These nodes are
	#         also data synchronization targets for 'sync' resources.
	#
	;drpnodes = []
	
	#
	# keyword:          encapnodes
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         []
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         list_lower
	#
	#  desc:  The list of containers handled by this service and with an OpenSVC
	#         agent installed to handle the encapsulated resources. With this
	#         parameter set, parameters can be scoped with the @encapnodes suffix.
	#
	;encapnodes = []
	
	#
	# keyword:          app
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         DEFAULT
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Used to identify who is responsible for this service, who is
	#         billable and provides a most useful filtering key. Better keep it a
	#         short code.
	#
	;app = DEFAULT
	
	#
	# keyword:          comment
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Helps users understand the role of the service, which is nice to on-
	#         call support people having to operate on a service they are not
	#         usually responsible for.
	#
	;comment = foo
	
	#
	# keyword:          scsireserv
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         False
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
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
	# keyword:          bwlimit
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         speed_kps
	#
	#  desc:  Bandwidth limit in KB applied to all rsync transfers. Leave empty to
	#         enforce no limit.
	#
	;bwlimit = 3 mb/s
	
	#
	# keyword:          sync_interval
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         121
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         duration
	#
	#  desc:  Set the minimum delay between syncs in minutes. If a sync is
	#         triggered through a scheduler or manually, it is skipped if last
	#         sync occurred less than 'sync_min_delay' ago. The mecanism is
	#         enforced by a timestamp created upon each sync completion in
	#         <pathvar>/sync/[service]![dst]
	#
	;sync_interval = 121
	
	#
	# keyword:          sync_max_delay
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         1440
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         duration
	#
	#  desc:  Unit is minutes. This sets to delay above which the sync status of
	#         the resource is to be considered down. Should be set according to
	#         your application service level agreement. The scheduler task
	#         frequency should be set between 'sync_min_delay' and
	#         'sync_max_delay'
	#
	;sync_max_delay = 1440
	
	#
	# keyword:          presnap_trigger
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         shlex
	#
	#  desc:  Define a command to run before creating snapshots. This is most
	#         likely what you need to use plug a script to put you data in a
	#         coherent state (alter begin backup and the like).
	#
	;presnap_trigger = /srv/svc1/etc/init.d/pre_snap.sh
	
	#
	# keyword:          postsnap_trigger
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         shlex
	#
	#  desc:  Define a command to run after snapshots are created. This is most
	#         likely what you need to use plug a script to undo the actions of
	#         'presnap_trigger'.
	#
	;postsnap_trigger = /srv/svc1/etc/init.d/post_snap.sh
	
	#
	# keyword:          pre_monitor_action
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A script to execute before the monitor_action. For example, if the
	#         monitor_action is set to freezestop, the script can decide to crash
	#         the server if it detects a situation were the freezestop can not
	#         succeed (ex. fs can not be umounted with a dead storage array).
	#
	;pre_monitor_action = /bin/true
	
	#
	# keyword:          monitor_action
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      reboot | crash | freezestop
	#
	#  desc:  The action to take when a monitored resource is not up nor standby
	#         up, and if the resource restart procedure has failed.
	#
	;monitor_action = reboot
	
	#
	# keyword:          create_pg
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         True
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  Use process containers when possible. Containers allow capping
	#         memory, swap and cpu usage per service. Lxc containers are naturally
	#         containerized, so skip containerization of their startapp.
	#
	;create_pg = True
	
	#
	# keyword:          pg_cpus
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#
	#  desc:  Allow service process to bind only the specified cpus. Cpus are
	#         specified as list or range : 0,1,2 or 0-2
	#
	;pg_cpus = 0-2
	
	#
	# keyword:          pg_mems
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#
	#  desc:  Allow service process to bind only the specified memory nodes.
	#         Memory nodes are specified as list or range : 0,1,2 or 0-2
	#
	;pg_mems = 0-2
	
	#
	# keyword:          pg_cpu_shares
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#  convert:         integer
	#
	#  desc:  Kernel default value is used, which usually is 1024 shares. In a
	#         cpu-bound situation, ensure the service does not use more than its
	#         share of cpu ressource. The actual percentile depends on shares
	#         allowed to other services.
	#
	;pg_cpu_shares = 512
	
	#
	# keyword:          pg_cpu_quota
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
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
	# keyword:          pg_mem_oom_control
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#  convert:         integer
	#
	#  desc:  A flag (0 or 1) that enables or disables the Out of Memory killer
	#         for a cgroup. If enabled (0), tasks that attempt to consume more
	#         memory than they are allowed are immediately killed by the OOM
	#         killer. The OOM killer is enabled by default in every cgroup using
	#         the memory subsystem; to disable it, write 1.
	#
	;pg_mem_oom_control = 1
	
	#
	# keyword:          pg_mem_limit
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#  convert:         size
	#
	#  desc:  Ensures the service does not use more than specified memory (in
	#         bytes). The Out-Of-Memory killer get triggered in case of
	#         tresspassing.
	#
	;pg_mem_limit = 512000000
	
	#
	# keyword:          pg_mem_swappiness
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#  convert:         integer
	#
	#  desc:  Set a swappiness value for the process group.
	#
	;pg_mem_swappiness = 40
	
	#
	# keyword:          pg_vmem_limit
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#  convert:         size
	#
	#  desc:  Ensures the service does not use more than specified memory+swap (in
	#         bytes). The Out-Of-Memory killer get triggered in case of
	#         tresspassing. The specified value must be greater than pg_mem_limit.
	#
	;pg_vmem_limit = 1024000000
	
	#
	# keyword:          pg_blkio_weight
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  depends:         create_pg in [True]
	#  convert:         integer
	#
	#  desc:  Block IO relative weight. Value: between 10 and 1000. Kernel
	#         default: 1000.
	#
	;pg_blkio_weight = 50
	
	#
	# keyword:          disable
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         False
	#  inheritance:     leaf
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  A disabled resource will be ignored on service startup and shutdown.
	#
	;disable = False
	
	#
	# keyword:          restart
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         0
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         integer
	#
	#  desc:  The agent will try to restart a resource n times before falling back
	#         to the monitor action.
	#
	;restart = 0
	
	#
	# keyword:          tags
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         set([])
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         set
	#
	#  desc:  A list of tags. Arbitrary tags can be used to limit action scope to
	#         resources with a specific tag. Some tags can influence the driver
	#         behaviour. For example the 'encap' tag assigns the resource to the
	#         encapsulated service, 'noaction' avoids any state changing action
	#         from the driver, 'nostatus' forces the status to n/a.
	#
	;tags = set([])
	
	#
	# keyword:          subset
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf
	#  scope order:     specific > generic
	#
	#  desc:  Assign the resource to a specific subset.
	#
	;subset = foo
	
	#
	# keyword:          monitor
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         False
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  A down monitored resource will trigger a node suicide if the monitor
	#         thinks it should be up and the resource can not be restarted.
	#
	;monitor = False
	
	#
	# keyword:          disable
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         False
	#  inheritance:     leaf
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  A disabled resource will be ignored on service startup and shutdown.
	#
	;disable = False
	
	#
	# keyword:          optional
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         True for task, sync and stonith, else False
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  Possible values are 'true' or 'false'. Actions on resource will be
	#         tried upon service startup and shutdown, but action failures will be
	#         logged and passed over. Useful for resources like dump filesystems
	#         for example.
	#
	;optional = True for task, sync and stonith, else False
	
	#
	# keyword:          always_on
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    False
	#  default:         []
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      nodes | drpnodes ...
	#  convert:         list
	#
	#  desc:  Possible values are 'nodes', 'drpnodes' or 'nodes drpnodes', or a
	#         list of nodes. Sets the nodes on which the resource is always kept
	#         up. Primary usage is file synchronization receiving on non-shared
	#         disks. Don't set this on shared disk !! danger !!
	#
	;always_on = []
	
	#
	# keyword:          provision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         True
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  Set to false to skip the resource on provision and unprovision
	#         actions. Warning: provisioning implies destructive operations like
	#         formating.
	#
	;provision = True
	
	#
	# keyword:          shared
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         False
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      True | False
	#  convert:         boolean
	#
	#  desc:  Set to True to skip the resource on provision and unprovision
	#         actions if the action has already been done by a peer. Shared
	#         resources, like vg built on SAN disks must be provisioned once.
	#
	;shared = False
	
	#
	# keyword:          pre_unprovision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource unprovision
	#         action. Errors do not interrupt the action.
	#
	;pre_unprovision = foo
	
	#
	# keyword:          post_unprovision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource unprovision
	#         action. Errors do not interrupt the action.
	#
	;post_unprovision = foo
	
	#
	# keyword:          pre_provision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource provision action.
	#         Errors do not interrupt the action.
	#
	;pre_provision = foo
	
	#
	# keyword:          post_provision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource provision action.
	#         Errors do not interrupt the action.
	#
	;post_provision = foo
	
	#
	# keyword:          pre_start
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource start action.
	#         Errors do not interrupt the action.
	#
	;pre_start = foo
	
	#
	# keyword:          post_start
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource start action.
	#         Errors do not interrupt the action.
	#
	;post_start = foo
	
	#
	# keyword:          pre_stop
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource stop action.
	#         Errors do not interrupt the action.
	#
	;pre_stop = foo
	
	#
	# keyword:          post_stop
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource stop action.
	#         Errors do not interrupt the action.
	#
	;post_stop = foo
	
	#
	# keyword:          blocking_pre_unprovision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource unprovision
	#         action. Errors interrupt the action.
	#
	;blocking_pre_unprovision = foo
	
	#
	# keyword:          blocking_post_unprovision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource unprovision
	#         action. Errors interrupt the action.
	#
	;blocking_post_unprovision = foo
	
	#
	# keyword:          blocking_pre_provision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource provision action.
	#         Errors interrupt the action.
	#
	;blocking_pre_provision = foo
	
	#
	# keyword:          blocking_post_provision
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource provision action.
	#         Errors interrupt the action.
	#
	;blocking_post_provision = foo
	
	#
	# keyword:          blocking_pre_start
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource start action.
	#         Errors interrupt the action.
	#
	;blocking_pre_start = foo
	
	#
	# keyword:          blocking_post_start
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource start action.
	#         Errors interrupt the action.
	#
	;blocking_post_start = foo
	
	#
	# keyword:          blocking_pre_stop
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource stop action.
	#         Errors interrupt the action.
	#
	;blocking_pre_stop = foo
	
	#
	# keyword:          blocking_post_stop
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource stop action.
	#         Errors interrupt the action.
	#
	;blocking_post_stop = foo
	
	#
	# keyword:          unprovision_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'unprovision' action. A condition is expressed as
	#         <rid>(<state>,...). If states are omitted, 'up,stdby up' is used as
	#         the default expected states.
	#
	;unprovision_requires = 
	
	#
	# keyword:          provision_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'provision' action. A condition is expressed as
	#         <rid>(<state>,...). If states are omitted, 'up,stdby up' is used as
	#         the default expected states.
	#
	;provision_requires = 
	
	#
	# keyword:          start_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'start' action. A condition is expressed as <rid>(<state>,...). If
	#         states are omitted, 'up,stdby up' is used as the default expected
	#         states.
	#
	;start_requires = 
	
	#
	# keyword:          stop_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'stop' action. A condition is expressed as <rid>(<state>,...). If
	#         states are omitted, 'up,stdby up' is used as the default expected
	#         states.
	#
	;stop_requires = 
	
	#
	# keyword:          pre_sync_nodes
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_nodes
	#         action. Errors do not interrupt the action.
	#
	;pre_sync_nodes = foo
	
	#
	# keyword:          post_sync_nodes
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_nodes action.
	#         Errors do not interrupt the action.
	#
	;post_sync_nodes = foo
	
	#
	# keyword:          pre_sync_drp
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_drp action.
	#         Errors do not interrupt the action.
	#
	;pre_sync_drp = foo
	
	#
	# keyword:          post_sync_drp
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_drp action.
	#         Errors do not interrupt the action.
	#
	;post_sync_drp = foo
	
	#
	# keyword:          pre_sync_restore
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_restore
	#         action. Errors do not interrupt the action.
	#
	;pre_sync_restore = foo
	
	#
	# keyword:          post_sync_restore
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_restore
	#         action. Errors do not interrupt the action.
	#
	;post_sync_restore = foo
	
	#
	# keyword:          pre_sync_resync
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_resync
	#         action. Errors do not interrupt the action.
	#
	;pre_sync_resync = foo
	
	#
	# keyword:          post_sync_resync
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_resync
	#         action. Errors do not interrupt the action.
	#
	;post_sync_resync = foo
	
	#
	# keyword:          pre_sync_update
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_update
	#         action. Errors do not interrupt the action.
	#
	;pre_sync_update = foo
	
	#
	# keyword:          post_sync_update
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_update
	#         action. Errors do not interrupt the action.
	#
	;post_sync_update = foo
	
	#
	# keyword:          blocking_pre_sync_nodes
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_nodes
	#         action. Errors interrupt the action.
	#
	;blocking_pre_sync_nodes = foo
	
	#
	# keyword:          blocking_post_sync_nodes
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_nodes action.
	#         Errors interrupt the action.
	#
	;blocking_post_sync_nodes = foo
	
	#
	# keyword:          blocking_pre_sync_drp
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_drp action.
	#         Errors interrupt the action.
	#
	;blocking_pre_sync_drp = foo
	
	#
	# keyword:          blocking_post_sync_drp
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_drp action.
	#         Errors interrupt the action.
	#
	;blocking_post_sync_drp = foo
	
	#
	# keyword:          blocking_pre_sync_restore
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_restore
	#         action. Errors interrupt the action.
	#
	;blocking_pre_sync_restore = foo
	
	#
	# keyword:          blocking_post_sync_restore
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_restore
	#         action. Errors interrupt the action.
	#
	;blocking_post_sync_restore = foo
	
	#
	# keyword:          blocking_pre_sync_resync
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_resync
	#         action. Errors interrupt the action.
	#
	;blocking_pre_sync_resync = foo
	
	#
	# keyword:          blocking_post_sync_resync
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_resync
	#         action. Errors interrupt the action.
	#
	;blocking_post_sync_resync = foo
	
	#
	# keyword:          blocking_pre_sync_update
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource sync_update
	#         action. Errors interrupt the action.
	#
	;blocking_pre_sync_update = foo
	
	#
	# keyword:          blocking_post_sync_update
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource sync_update
	#         action. Errors interrupt the action.
	#
	;blocking_post_sync_update = foo
	
	#
	# keyword:          sync_nodes_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_nodes' action. A condition is expressed as
	#         <rid>(<state>,...). If states are omitted, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_nodes_requires = 
	
	#
	# keyword:          sync_drp_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_drp' action. A condition is expressed as <rid>(<state>,...).
	#         If states are omitted, 'up,stdby up' is used as the default expected
	#         states.
	#
	;sync_drp_requires = 
	
	#
	# keyword:          sync_update_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_update' action. A condition is expressed as
	#         <rid>(<state>,...). If states are omitted, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_update_requires = 
	
	#
	# keyword:          sync_break_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_break' action. A condition is expressed as
	#         <rid>(<state>,...). If states are omitted, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_break_requires = 
	
	#
	# keyword:          sync_resync_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_resync' action. A condition is expressed as
	#         <rid>(<state>,...). If states are omitted, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_resync_requires = 
	
	#
	# keyword:          sync_restore_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_restore' action. A condition is expressed as
	#         <rid>(<state>,...). If states are omitted, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_restore_requires = 
	
	#
	# keyword:          run_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'run' action. A condition is expressed as <rid>(<state>,...). If
	#         states are omitted, 'up,stdby up' is used as the default expected
	#         states.
	#
	;run_requires = 
	
	#
	# keyword:          pre_run
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource run action.
	#         Errors do not interrupt the action.
	#
	;pre_run = foo
	
	#
	# keyword:          post_run
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource run action. Errors
	#         do not interrupt the action.
	#
	;post_run = foo
	
	#
	# keyword:          blocking_pre_run
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute before the resource run action.
	#         Errors interrupt the action.
	#
	;blocking_pre_run = foo
	
	#
	# keyword:          blocking_post_run
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command or script to execute after the resource run action. Errors
	#         interrupt the action.
	#
	;blocking_post_run = foo
	
	#
	# keyword:          run_requires
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'run' action. A condition is expressed as <rid>(<state>,...). If
	#         states are omitted, 'up,stdby up' is used as the default expected
	#         states.
	#
	;run_requires = 
	
