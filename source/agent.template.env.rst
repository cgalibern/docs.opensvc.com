Service configuration file template
***********************************

Here is a copy of the template service env file available on the nodes at ``/opt/opensvc/usr/share/doc/template.env``::


	#
	# OpenSVC config files are written in standard ini file format:
	#
	# "The configuration file consists of sections, led by a [section] header and
	# followed by name: value entries, with continuations in the style of RFC 822
	# (see section 3.1.1, “LONG HEADER FIELDS”); name=value is also accepted. Note
	# that leading whitespace is removed from values.
	# Lines beginning with '#' or ';' are ignored and may be used to provide
	# comments."
	#               extract from http://docs.python.org/library/configparser.html
	#
	# Resource are label [resource_name#index_in_resourse_set], like [ip#1],
	# [ip#2], [fs#1], [fs#2]...
	#
	# Every resource accept these options:
	# 'disable'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   A disabled resource will be ignored on service startup and shutdown.
	#
	# 'disable_on'
	#   optional. A list of nodenames where to consider the 'disable' value is
	#   True. Also accepts the keywords 'nodes' and 'drpnodes'.
	#
	# 'optional'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   Actions on resource will be tried upon service startup and shutdown,
	#   but action failures will be logged and passed over. Useful for resources
	#   like dump filesystems for example.
	#
	# 'optional_on'
	#   optional. A list of nodenames where to consider the 'optional' value is
	#   True. Also accepts the keywords 'nodes' and 'drpnodes'.
	#
	# 'monitor'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to 'true' the resource being down when the heartbeat thinks the
	#   service should be 'up' triggers the execution of the 'monitor_action'.
	#
	# 'monitor_on'
	#   optional. A list of nodenames where to consider the 'monitor' value is
	#   True. Also accepts the keywords 'nodes' and 'drpnodes'.
	#
	# 'restart'
	#   optional. Integer values. Default is 0.
	#   Set the number of start to be attempted on a not-up resource by the
	#   resource monitor action. If the resource is also flagged for monitoring
	#   this parameter would allow to abort the TOC if the failed resource
	#   is succesfully restarted.
	#
	# 'subset'
	#   optional. A subset identifier. If set, the resource joins the specified
	#   resource subset. A subset can have special properties, like parallel
	#   action execution amongst its members.
	#
	# 'pre_start'
	# 'post_start'
	# 'pre_stop'
	# 'post_stop'
	# 'pre_syncnodes'
	# 'post_syncnodes'
	# 'pre_syncdrp'
	# 'post_syncdrp'
	# 'pre_syncresync'
	# 'post_syncresync'
	#   optional. A command or script to exec before or after the resource
	#   action. Arguments can be passed, but a single command is accepted.
	#
	#
	# Every service config file must have a DEFAULT section.
	#

	##############################################################################
	#
	# Main service definition
	#
	##############################################################################

	[DEFAULT]
	#
	# 'app'
	#   is used to identify who is responsible for is service, who is billable
	#   and provides a most useful filtering key. Better keep it a short code.
	#
	;app = OSVC

	#
	# 'comment'
	#   is optional, but helps users understand the role of the service, 
	#   which is nice to on-call support people having to operate on a
	#   service they are usualy responsible for.
	#
	;comment = opensvc web front-end

	#
	# 'mode'
	#   supported modes are 'hosted', 'sg' or 'rhcs'. The default is 'hosted'.
	#   the mode decides upon disposition OpenSVC takes to bring a service up
	#   or down. Tiers cluster modes for example inihibit stop*/start* actions,
	#   auto-discovers resources and asks the tiers clusterware for resource
	#   status.
	#
	;mode = hosted

	#
	# 'drp_type'
	#   supported values are 'standby' or 'srdf'. The default is 'standby'.
	#   Not used for the moment.
	#
	;drp_type = standby

	#
	# 'service_type'
	#   supported values are 'DEV' and 'PRD'. There is no default, and this
	#   setting is mandatory, as important rules apply to it :
	#   1/ a DEV service can not be brought up on a PRD node, but a PRD service
	#      can be startup on a DEV node (in a DRP situation).
	#
	;service_type = DEV

	#
	# 'encapnodes'
	#   optional list of virtual nodes in charge of the encapsulated service
	#   described in this service configuration file. If set, other parameters
	#   can be scoped using the 'param@encapnodes = ' syntax.
	#   Not setting 'encapnodes' or setting it to an empty list disables the
	#   encapsulated service management.
	#
	;encapnodes = vm1 vm2

	#
	# 'nodes'
	#   mandatory list of cluster nodes able to start the service when not in
	#   a DRP situation
	#
	;nodes = titan

	#
	# 'autostart_node'
	#   A subset of 'nodes' where the service will try to start on upon node
	#   reboot. On a failover cluster only one autostart_node should be
	#   defined, and the start-up will fail if the service is already up on another
	#   node.
	#   If not specified, the service will never be started at node boot-time,
	#   which is rarely the expected behaviour.
	#
	;autostart_node = titan

	#
	# 'cluster'
	#   Optional. The symbolic name of the cluster.
	#
	;cluster = clu1

	#
	# 'anti_affinity'
	#   a whitespace separated list of services this service is not
	#   allowed to be started on the same node. The svcmgr --ignore-affinity
	#   option can be set to override this policy.
	#
	;anti_affinity = svc2 svc3

	#
	# 'cluster_type'
	#   Optional. Defaults to 'failover'.
	#   Allowed values:
	#
	#   'failover'
	#      The service can be up only on one node at a time. 
	#
	#   'flex'
	#      The service can be up on multiple nodes simultaneously.
	#
	#   'autoflex'
	#      Like flex, and allows the collector to start and stop instances.
	#
	#
	;cluster_type = failover

	#
	# 'flex_primary'
	#   the nodename of the node allowed to sync to other flex nodes.
	#
	;flex_primary = titan

	#
	# 'flex_min_nodes'
	#   Default: 1
	#   the minimum number of nodes where the service should be up.
	#   Alerts are raised on the collector upon crossing this limit.
	#   On autoflex, the collector would not trigger actions that would
	#   put the service out of bounds.
	#
	;flex_min_nodes = 1

	#
	# 'flex_max_nodes'
	#   Default: the total number of nodes
	#   the maximum number of nodes where the service should be up.
	#   Alerts are raised on the collector upon crossing this limit.
	#   On autoflex, the collector would not trigger actions that would
	#   put the service out of bounds.
	#
	;flex_max_nodes = 10

	#
	# 'flex_cpu_low_threshold'
	#   Default: 10
	#   the minimum percentile of average node cpu usage.
	#   Alerts are raised on the collector upon crossing this limit.
	#   On autoflex, the collector would trigger actions to keep the cpu
	#   usage in bounds.
	#
	;flex_cpu_low_threshold = 10

	#
	# 'flex_cpu_high_threshold'
	#   Default: 10
	#   the maximum percentile of average node cpu usage.
	#   Alerts are raised on the collector upon crossing this limit.
	#   On autoflex, the collector would trigger actions to keep the cpu
	#   usage in bounds.
	#
	;flex_cpu_high_threshold = 90

	#
	# 'drpnode'
	#   optional. The backup node where the service is activated in a DRP
	#   situation. This node is also a data synchronization target for 'sync'
	#   resources (see below)
	#
	;drpnode = vm5

	#
	# 'drpnodes'
	#   optional. Alternate backup nodes, where the service could be activated
	#   in a DRP situation if the 'drpnode' is not available. These nodes are
	#   also data synchronization targets for 'sync' resources (see below)
	#
	;drpnodes = vm6 vm7

	#
	# 'scsireserv'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to 'true', OpenSVC will try to acquire a type-5 (write exclusive,
	#   registrant only) scsi3 persistent reservation on every path to disks of
	#   every disk group attached to this service. Existing reservations are
	#   preempted to not block service start-up. If the start-up was not
	#   legitimate the data are still protected from being written over from both
	#   nodes.
	#   If set to 'false' or not set, 'scsireserv' can be activated on a per-
	#   resource basis.
	#
	;scsireserv = false

	#
	# 'no_preempt_abort'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to 'true', OpenSVC will preempt scsi reservation with a preempt
	#   command instead of a preempt and and abort. Some scsi target
	#   implementations do not support this last mode.
	#   If set to 'false' or not set, 'no_preempt_abort' can be activated on a
	#   per-resource basis.
	#
	;no_preempt_abort = False

	#
	# 'bwlimit'
	#   optional. Bandwidth limit in KB applied to all rsync transfers
	#
	;bwlimit = 3000

	#
	# 'sync_interval'
	#   optional. Set the minimum delay between syncs in minutes. If a sync is
	#   triggered through crond or manually, it is skipped if last sync occured
	#   less than 'sync_interval' ago. 
	#   The mecanism is enforced by a timestamp created upon each sync completion
	#   in /opt/opensvc/var/sync/[service]![dst]
	#
	;sync_interval = 30

	#
	# 'sync_days'
	#   optional. Defaults to 'every week day'.
	#   Set the days this resource synchronization is allowed.
	#
	;sync_days = ["monday", "friday"]

	#
	# 'sync_period'
	#   optional. Defaults to 4am to 6am.
	#   Set the time ranges this resource synchronization is allowed.
	#
	;sync_period = ["04:00", "06:00"]
	;sync_period = [["04:00", "06:00"], ["18:00", "20:00"]]

	#
	# 'sync_interval'
	#   optional. Set the minimum delay between syncs in minutes. If a sync is
	#   triggered through crond or manually, it is skipped if last sync occured
	#   less than 'sync_interval' ago. 
	#   The mecanism is enforced by a timestamp created upon each sync completion
	#   in /opt/opensvc/var/sync/[service]![dst]
	#
	;sync_interval = 30

	#
	# 'sync_max_delay'
	#   optional. Default value is 1440 minutes (1 day). Unit is minutes.
	#   This sets to delay above which the sync status of the resource is to be
	#   considered down. Should be set according to your application service
	#   level agreement. The cron job frequency should be set between
	#   'sync_interval' and 'sync_max_delay'.
	#
	;sync_max_delay = 1440

	#
	# 'presnap_trigger'
	#   optional. Defaults to None. Define a command to run before creating
	#   snapshots. This is most likely what you need to use plug a script to
	#   put you data in a coherent state (alter begin backup and the like).
	# 
	;presnap_trigger = /bin/true

	#
	# 'postsnap_trigger'
	#   optional. Defaults to None. Define a command to run after snapshots are
	#   created. This is most likely what you need to use plug a script to
	#   undo the actions of 'presnap_trigger'.
	# 
	;postsnap_trigger = /bin/true

	#
	# 'containerize'
	#   optional. Defaults to true. Use process containers when possible.
	#   Containers allow capping memory, swap and cpu usage per service.
	#   Lxc containers are naturally containerized, so skip containerization
	#   of their startapp.
	# 
	;containerize = false

	#
	# 'container_cpus'
	#   optional. Defaults to all cpus. Allow service process to bind only
	#   the specified cpus. Cpus are specified as list or range : 0,1,2 or
	#   0-2
	# 
	;container_cpus = 0-1

	#
	# 'container_mems'
	#   optional. Defaults to all memory nodes. Allow service process to bind
	#   only the specified memory nodes. Memory nodes are specified as list or
	#   range : 0,1,2 or 0-2
	# 
	;container_mems = 0

	#
	# 'container_cpu_share'
	#   optional. No default, kernel default value is used, which usually is
	#   1024 shares. In a cpu-bound situation, ensure the service does not
	#   use more than its share of cpu ressource. The actual percentile depends
	#   on shares allowed to other services.
	# 
	;container_cpu_share = 1024

	#
	# 'container_mem_limit'
	#   optional. Defaults to all available memory. Ensures the service does
	#   not use more than specified memory (in bytes). The Out-Of-Memory killer
	#   get triggered in case of tresspassing.
	# 
	;container_mem_limit = 100000000

	#
	# 'container_vmem_limit'
	#   optional. Defaults to all available memory+swap. Ensures the service does
	#   not use more than specified memory+swap (in bytes). The Out-Of-Memory killer
	#   get triggered in case of tresspassing. The specified value must be greater
	#   than container_mem_limit
	# 
	;container_vmem_limit = 200000000

	#
	# 'monitor_action'
	#   optional. Possible values are 'freezestop', 'reboot' or 'crash'.
	#   If the service has a heartbeat resource and some resources are flagged
	#   as monitored, in the event the heartbeat reports 'up' and some
	#   monitored resource reports 'not up', the monitor action is triggered
	#   through svcmon cron job or a user-added 'resource_monitor' action
	#   schedule.
	#
	;monitor_action = freezestop

	#
	# 'docker_data_dir'
	#  scopable: true
	#  if the service has docker-type container resources, the service handles
	#  the startup of a private docker daemon. Its socket is /opt/opensvc/var/
	#  <svcname</docker.sock, and its data dirextory must be specified using this
	#  parameter. This organization is necessary to enable service relocalization.
	#
	;docker_data_dir = /srv/mysvc/docker

	#
	# 'docker_daemon_args'
	#  scopable: true
	#  if the service has docker-type container resources, the service handles
	#  the startup of a private docker daemon. OpenSVC sets the socket and
	#  data dir parameters. Admins can set extra parameters using this keyword.
	#  For example, it can be useful to set the --ip parameter for a docker
	#  registry service.
	#
	;docker_daemon_args = --ip 1.2.3.4


	##############################################################################
	#
	# Service resource subsets
	#
	##############################################################################

	;[subset#app:0]

	#
	# 'parallel'
	#   optional. default is false.
	#   If set to true, actions are executed in parallel amongst the subset member
	#   resources.
	#
	;parallel = true


	##############################################################################
	#
	# Service resources
	#
	##############################################################################

	##############################################################################
	#
	# 'app' resources
	#   Application launchers
	#
	;[app#0]
	;optional = true
	;disable = false
	;always_on = drpnodes

	#
	# 'script'
	#   mandatory.
	#   The script to execute. If a basename is defined, the full path to
	#   <svcname>.d will be prepended.
	#
	;script = feed_queue

	#
	# 'start'
	#   default: None
	#   Execute the script on service start, with the 'start' parameter,
	#   if set to a sequence number.
	#
	;start = 50

	#
	# 'stop'
	#   default: None
	#   Execute the script on service stop, with the 'stop' parameter,
	#   if set to a sequence number.
	#
	;stop = 50

	#
	# 'check'
	#   default: None
	#   Execute the script on service status eval, with the 'status' parameter,
	#   if set to a sequence number.
	#
	;check = 50

	#
	# 'info'
	#   default: None
	#   Execute the script on service push appinfo, with the 'info' parameter,
	#   if set to a sequence number.
	#
	;info = 50

	#
	# 'subset'
	#   default: None
	#   Execute the script in a resource subset. The subset can be flagged for
	#   parallel action execution amongst its member resources.
	#
	;subset = 1

	#
	# 'timeout'
	#   default: None
	#   Wait for <n> seconds max before declaring the app launcher action a
	#   failure. If no timeout is specified, the agent waits indefinitely for the
	#   app launcher to return. The timeout parameter can be coupled with
	#   optional=True to not abort a service start when an app launcher did not
	#   return.
	#
	;timeout = 180


	##############################################################################
	#
	# 'container' resources
	#   describe which container to drive for the service. Any number of containers
	#   can be attached to the service.
	#   If the container is already started on another node the service refuses
	#   to start.
	#   A container can have a list of disks. As such the 'scsireserv' and
	#   'no_preemt_abort' parameters can be set. 
	#
	;[container#0]

	#
	# 'type'
	#   defines the container the virtualization driver for this container.
	#   possible values are 'ldom', 'hpvm', 'kvm', 'xen', 'vbox', 'ovm', 'esx',
	#   'zone', 'lxc', 'jail', 'vz', 'srp', 'vcloud', 'openstack', 'docker'
	#
	;type = kvm

	#
	# 'name'
	#   defines the container name as reported by the virtualization technology.
	#   'vz' uses only ids, so a valid name can be '101".
	#
	;name = vm1

	#
	# 'uuid'
	#   'ovm' needs this parameter set to the vm uuid.
	#
	;uuid = 70afba94-84bf-49a3-bc8e-cea320c98028

	#
	# 'guestos'
	#   optional. defaults to the hypervisor os. sets the guest operating system
	#   inside the container handled by the service. Used to switch to proper
	#   per-os routines.
	#
	;guestos = Windows

	#
	# 'cf'
	#  'lxc'-type resources can set this parameter to point their container config
	#  file.
	#
	;cf = /srv/mycontainer/config


	#
	# Docker specific container parameter
	#

	;type = docker

	#
	# 'run_image'
	#  docker image to run when no container named <svcnme>.<rid> exists.
	#
	;run_image = 83f2a3dd2980

	#
	# 'run_commond'
	#  command to execute in the docker image run when no container named
	#  <svcnme>.<rid> exists. When the container already exists, the command
	#  in its metadata take precedence.
	#
	;run_command = /opt/tomcat/bin/catalina.sh


	#
	# 'run_args'
	#  additional arguments to pass upon docker image run
	#
	;run_args = -v /opt/docker.opensvc.com/vol1:/vol1:rw -p 37.59.71.25:8080:8080

	##############################################################################
	#
	# 'ip' resources
	#   describe which ip to plumb for the service. Any number of ips can be
	#   attached to the service, but ips are to be uniquely assigned to it.
	#   In case of ip conflict, the service refuses to start.
	#

	;[ip#1]
	;disable = true
	;disable_on = node12 node21
	;optional = true
	;optional_on = node12 node21
	;monitor = true
	;monitor_on = node12 node21
	;restart = 1

	#
	# 'tags'
	#    
	#   encap
	#    this tag tells opensvc to handle this resource using the agent
	#    embedded in the service containers instead of the master agent.
	#    The resource status is also evaluated by the slave agents and
	#    handed to the master agent as a json structure.
	#    
	#   noalias
	#    tells opensvc not to stack an ip alias but to plumb the ip on
	#    the base ethernet interface. in this case, the netmask parameter
	#    must be set for the resource as opensvc can not deduce the
	#    netmask from the interface primary ip.
	#    
	#   noaction
	#    disables the stop and start actions for the resource. The status
	#    is still evaluated though. This tag can be used to describe
	#    container ips activated and desactivated by the container boot
	#    and shutdown sequence.
	#
	;tags = encap noaction

	# 'ipname'
	#   the DNS name of the ip resource. Can be different from one node to the
	#   other, in which case '@nodename' can be specified. This is most
	#   useful to specify a different ip when the service starts in DRP mode,
	#   where subnets are likely to be different than those of the production
	#   datacenter.
	#
	;ipname@titan = unxdevweb
	;ipname@vm5 = unxdrpweb

	#
	# 'ipdev'
	#   the interface name over which OpenSVC will try to stack the service
	#   ip. Can be different from one node to the other, in which case the
	#   '@nodename' can be specified.
	#
	;ipdev@titan = br0
	;ipdev@vm5 = eth0

	#
	# 'netmask'
	#   optional if an ip is already plumbed on the root interface (if which
	#   case the netmask is deduced from this ip). Mandatory if the interface
	#   is dedicated to the service (dummy interface are likely to be in this
	#   case).
	#   the format is decimal, ex: 255.255.252.0
	#
	;netmask = 255.255.255.0

	#
	# 'always_on'
	#   optional. Possible values are 'nodes', 'drpnodes' or 'nodes drpnodes',
	#   or a list of nodes.
	#   Sets the nodes on which the resource is always kept up. Primary usage is
	#   file synchronization receiving on non-shared disks. Don't set this on
	#   shared disk !! danger !!
	#
	;always_on = drpnodes

	#
	# 'zone'
	#   optional. 
	#   This resource will start after the referenced zone startup.
	#
	;zone = zname


	##############################################################################
	#
	# 'vg' resource
	#   Disk group in the sense of volume managers, whatever the implementation.
	#   Attaching a 'vg' to a service will make OpenSVC check and drive its
	#   imported/exported status.
	#
	;[vg#1]
	;disable = true
	;disable_on = node12 node21
	;optional = true
	;optional_on = node12 node21
	;monitor = true
	;monitor_on = node12 node21

	#
	# 'vgname'
	#   mandatory, expect for the raw vg type.
	#   The name of the volume group, as seen by the volume manager.
	#
	;vgname = unxtstsvc02

	#
	# 'dsf'
	#   optional. Boolean. HP-UX only. Default value is True.
	#   'dsf' must be set to false for LVM to use never-multipathed /dev/dsk/...
	#   devices. Otherwize, ad-hoc multipathed /dev/disk/... devices.
	#
	;dsf = true

	#
	# 'scsireserv'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to 'true', OpenSVC will try to acquire a type-5 (write exclusive,
	#   registrant only) scsi3 persistent reservation on every path to disks of
	#   every disk group attached to this service. Existing reservations are
	#   preempted to not block service start-up. If the start-up was not
	#   legitimate the data are still protected from being written over from both
	#   nodes.
	#   If set to 'false' or not set, 'scsireserv' can still be activated globally
	#   from the 'default' section.
	#
	;scsireserv = false

	#
	# 'no_preempt_abort'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to 'true', OpenSVC will preempt scsi reservation with a preempt
	#   command instead of a preempt and and abort. Some scsi target
	#   implementations do not support this last mode.
	#   If set to 'false' or not set, 'no_preempt_abort' can be activated on a
	#   per-resource basis.
	#
	;no_preempt_abort = False

	#
	# 'always_on'
	#   optional. Possible values are 'nodes', 'drpnodes' or 'nodes drpnodes',
	#   or a list of nodes.
	#   Sets the nodes on which the resource is always kept up. Primary usage is
	#   file synchronization receiving on non-shared disks. Don't set this on
	#   shared disk !! danger !!
	#
	;always_on = drpnodes

	#
	# 'type'
	#   optional.
	#   values: veritas, raw
	#   'type' may be set to veritas to use veritas volume group instead of native
	#   os volume group or raw to provide explicitely a set of device paths through
	#   the 'devs' parameter.
	#
	;type = veritas

	#
	# 'devs'
	#   mandatory for the 'raw' vg type.
	#   values: a list of device paths, whitespace separated.
	#   'devs' contains the raw-type volume group device paths list. Those devices
	#   are thus listed as owned by the service and scsi reservation policy is
	#   applied to them.
	#
	;devs = /dev/mapper/svc.d0 /dev/mapper/svc.d1

	##############################################################################
	#
	# 'pool' resource
	#   zfs pool the sense of volume managers, whatever the implementation.
	#   Attaching a ZFS 'pool' to a service will make OpenSVC check and drive its
	#   imported/exported status.
	#
	;[pool#1]
	;disable = true
	;disable_on = node12 node21
	;optional = true
	;optional_on = node12 node21
	;monitor = true
	;monitor_on = node12 node21

	#
	# 'poolname'
	#   nothing special there
	#
	;poolname = zpool

	#
	# 'scsireserv'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to 'true', OpenSVC will try to acquire a type-5 (write exclusive,
	#   registrant only) scsi3 persistent reservation on every path to disks of
	#   every disk group attached to this service. Existing reservations are
	#   preempted to not block service start-up. If the start-up was not
	#   legitimate the data are still protected from being written over from both
	#   nodes.
	#   If set to 'false' or not set, 'scsireserv' can still be activated globally
	#   from the 'default' section.
	#
	;scsireserv = false

	#
	# 'no_preempt_abort'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to 'true', OpenSVC will preempt scsi reservation with a preempt
	#   command instead of a preempt and and abort. Some scsi target
	#   implementations do not support this last mode.
	#   If set to 'false' or not set, 'no_preempt_abort' can be activated on a
	#   per-resource basis.
	#
	;no_preempt_abort = False

	#
	# 'always_on'
	#   optional. Possible values are 'nodes', 'drpnodes' or 'nodes drpnodes',
	#   or a list of nodes.
	#   Sets the nodes on which the resource is always kept up. Primary usage is
	#   file synchronization receiving on non-shared disks. Don't set this on
	#   shared disk !! danger !!
	#
	;always_on = drpnodes

	#
	# 'zone'
	#   optional. 
	#   This resource will start after the referenced zone startup.
	#
	;zone = zname


	##############################################################################
	#
	# 'drbd' resource
	#   Linux only. Set up the attachment, connection and role of a defined drbd
	#   resource. Depending on weather this resource is stacked over or under
	#   other disk group resources we need to start it respectively late or early.
	#   This is controlled by a set of tags: 'prevg', 'postvg'.
	#
	[drbd#0]

	#
	# 'res'
	#   mandatory. String. The name of the drbd resource associated with this
	#   service resource. OpenSVC expect the resource configuration file to
	#   reside in '/etc/drbd.d/resname.res'. The 'sync#i0' resource will take
	#   care of replicating this file to remote nodes.
	#
	res = data

	#
	# 'always_on'
	#   state the expected status on nodes specified as value is 'up'. With drbd
	#   the 'up' status is granted when the drbd driver reports UpToDate/UpToDate,
	#   so always_on should point to all nodes participating in the drbd resource.
	#
	always_on = drpnodes nodes

	#
	# 'tags'
	#    prevg:  upon service 'start', drbd 'start' is scheduled before volume
	#            group 'start'. To use when the volume group is layered over the
	#            drbd.
	#    postvg: upon service 'start', drbd 'start' is scheduled after volume 
	#            group 'start'. To use when the the drbd is layered over the
	#            volume group.
	#
	tags = prevg


	##############################################################################
	#
	# 'share' resource
	#   define a network share to setup upon service startup.
	#
	;[share#1]
	;disable = true
	;disable_on = node12 node21
	;optional = true
	;optional_on = node12 node21
	;monitor = true
	;monitor_on = node12 node21

	#
	# 'type'
	#   possible values:
	#       nfs

	;type = nfs

	#
	# 'path'
	#    the full path name of the filesystem tree to share, as you would
	#    set it in /etc/exports on Linux
	#
	;path = /opt/unxtstsvc01

	#
	# 'opts'
	#    the sharing options of the filesystem tree to pointed by path, as you
	#    would set it in /etc/exports on Linux
	#
	;opts = *(ro) client1(rw)

	 
	##############################################################################
	#
	# 'fs' resource
	#   describes filesystems to mount on service startup and umount on service
	#   shutdown.
	#   The options are aligned to the Unix fstab fields. Whatever is possibly
	#   described in the fstab should be supported in there.
	#
	;[fs#1]
	;disable = true
	;disable_on = node12 node21
	;optional = true
	;optional_on = node12 node21
	;monitor = true
	;monitor_on = node12 node21
	;dev = /opt/unxtstsvc01.img
	;mnt = /opt/unxtstsvc01
	;mnt_opt = rw,loop
	;type = ext4
	;zone = zname

	;[fs#2]
	;dev = zpool/app
	;mnt = /unxtstsvc01/app
	;type = zfs

	#
	# 'type'
	#   possible values:
	#       zfs lofs ext3 ext4 ...
	#

	#
	# 'dev'
	#   can have per-node value, using the 'dev@node' parameter syntax for
	#   each node. You can mix 'dev' with 'dev@node' syntax to obtain a default
	#   plus exceptions behaviour. This facility is most useful for replicating
	#   nas heads, when you want the nodes to use the closest head.
	# 
	;dev@prdnode = prdnas:/vol/vol1
	;dev@drpnode = drpnas:/vol/vol1


	#
	# 'always_on'
	#   optional. Possible values are 'nodes', 'drpnodes' or 'nodes drpnodes',
	#   or a list of nodes.
	#   Sets the nodes on which the resource is always kept up. Primary usage is
	#   file synchronization receiving on non-shared disks. Don't set this on
	#   shared disk !! danger !!
	#
	;always_on = drpnodes

	#
	# 'zone'
	#   optional. 
	#   This resource will start after the referenced zone startup. The zone
	#   path is prepended to the mnt parameter.
	#
	;zone = zname

	#
	# 'globalfs'
	#   optional. Defaults to false.
	#   If set to true, don't reparent the the fs mount to the zone path.
	#
	;globalfs = true

	##############################################################################
	#
	# 'loop' resource
	#   linux-only.
	#   describes a loop device attached to the service. startup triggers the
	#   allocation of a block device (usualy major 7) mapped over the specified
	#   file. The created loop dev can be used to stack disk group also attached
	#   to the service.
	#
	;[loop#1]
	;disable = true
	;disable_on = node12 node21
	;optional = true
	;optional_on = node12 node21
	;monitor = true
	;monitor_on = node12 node21
	;file = /opt/unxtstsvc02.img


	##############################################################################
	#
	# 'sync' resource
	#   describes a rsync-based data synchronization job. By default the sync
	#   is run daily.
	#
	;[sync#1]
	;disable = true
	;disable_on = node12 node21
	;optional = true
	;optional_on = node12 node21
	;monitor = true
	;monitor_on = node12 node21

	#
	# 'tags'
	#   the sync resource supports the 'delay_snap' tag. This tag is used to
	#   delay the snapshot creation just before the rsync, thus after 'postsnap_trigger'
	#   execution. The default behaviour (no tags) is to group all snapshots creation
	#   before copying data to remote nodes, thus between 'presnap_trigger' and
	#   'postsnap_trigger'.
	#
	;tags = delay_snap

	#
	# 'src'
	#   source of the sync. Can be a whitespace-separated list of files or dirs
	#   passed as-is to rsync. Beware of the meaningful ending '/'. Refer to
	#   the rsync man page for details.
	#
	;src = /unxdevweb/

	#
	# 'dst'
	#   destination of the sync. Beware of the meaningful ending '/'. Refer to
	#   the rsync man page for details.
	#
	;dst = /unxdevweb

	#
	# 'exclude'
	#   !deprecated!, optional. A whitespace-separated list of --exclude params
	#   passed unchanged to rsync. The 'options' keyword is preferred now.
	#
	;exclude = --exclude=cache

	#
	# 'options'
	#   optional. A whitespace-separated list of params passed unchanged to rsync.
	#   Typical usage is ACL preservation activation.
	#
	;options = -A

	#
	# 'target'
	#   mandatory. Possible values are 'nodes', 'drpnodes' or 'nodes drpnodes'.
	#   Describes which nodes should receive this data sync from the PRD node
	#   where the service is up and running.
	#
	#   SAN storage shared 'nodes' must not be sync to 'nodes'.
	#   SRDF-like paired storage must not be sync to 'drpnodes'.
	#
	;target = nodes drpnodes

	#
	# 'snap'
	#   optional. Possible values are 'true' or 'false'. Default is 'false'.
	#   If set to true, OpenSVC will try to snapshot the first snapshottable
	#   parent of the source of the sync and try to sync from the snap.
	#
	;snap = true

	#
	# 'dstfs'
	#   optional. If set to a remote mount point, OpenSVC will verify that the
	#   specified mount point is really hosting a mounted FS. This can be used
	#   as a safety net to not overflow the parent FS (may be root).
	#
	;dstfs = /remote/dir

	#
	# 'bwlimit'
	#   optional. Bandwidth limit in KB applied to this rsync transfer. Takes
	#   precedence over 'bwlimit' set in [DEFAULT].
	#
	;bwlimit = 3000

	#
	# 'sync_interval'
	#   optional. Set the minimum delay between syncs in minutes. If a sync is
	#   triggered through crond or manually, it is skipped if last sync occured
	#   less than 'sync_interval' ago. If no set in a resource section, fallback
	#   to the value set in the 'default' section. The mecanism is enforced by a
	#   timestamp created upon each sync completion in
	#   /opt/opensvc/var/sync/[service]![dst]
	#
	;sync_interval = 30

	#
	# 'type'
	#   optional. Default is 'rsync'. Specify a data sync mode. Supported values
	#   are: zfs, netapp, rsync, dds, btrfs
	#
	;type = netapp
	;type = zfs

	#
	# 'zfs' type specific parameter.
	#   The synchronization mecanism used is zfs send / zfs receive.
	#   src and dst may refer a dataset instead of directory
	#   src and dst can be different from one node to the
	#   other, in which case '@nodename' can be specified.
	#

	#
	# 'recursive'
	#   optional. (used when type = 'zfs')
	#   Default is 'True'. So snapshots are created recursivly
	#
	;recursive = False

	#
	# 'btrfs' type specific parameter.
	#   The synchronization mecanism used is btrfs send / btrfs receive.
	#   src and dst must be formatted as <label>:<subvol>
	#   src and dst can be different from one node to the
	#   other, in which case '@nodename', '@nodes' or '@drpnodes' can be
	#   specified.
	#   The destination must be umounted (do not set always_on on the
	#   the corresponding fs resources).
	#
	;src = mysvc_data:mysvc_root
	;dst = mysvc_data:mysvc_root
	;dst@drpnodes = shared_data:mysvc_root

	#
	# 'recursive'
	#   optional. (used when type = 'btrfs')
	#   Default is 'False'. Toggles recursive snapshots and sends.
	#   Btrfs does not yet support this feature. It is included in
	#   OpenSVC in anticipation.
	#
	;recursive = False

	#
	# 'netapp' type specific parameter.
	#   The synchronization mecanism used is snapmirror.
	#

	#
	# 'filer'
	#   mandatory. 'filer' points the nas head to pass commands to. In most case
	#   you need to specify localized filers using the 'filer@node' syntax.
	#
	;filer@vm4 = nasprd
	;filer@vm5 = nasdrp

	#
	# 'path'
	#   mandatory. Specifies the volume or qtree to drive snapmirror on.
	#
	;path = /vol/vol1

	#
	# 'user'
	#   mandatory. Specifies the user used to ssh connect the filers. Nodes should
	#   be trusted by keys to access the filer with this user.
	#
	;user = nasadm


	##############################################################################
	#
	# Symmetrix clones
	#
	;[sync#2]
	;type = symclone

	#
	# 'symdg'
	#   mandatory. name of the symmetrix device group where the source and target
	#   devices are grouped.
	#
	;symdg = DGCVI

	#
	# 'precopy_timeout'
	#   optional. default 300 secs. seconds to wait for a precopy (syncresync) to
	#   finish before returning with an error. In this case, the precopy proceeds
	#   normally, but the opensvc leftover actions must be retried. The precopy
	#   time depends on the amount of changes logged at the source, which is
	#   context-dependent. Tune to your needs.
	#
	;precopy_timeout = 300

	#
	# 'symdevs'
	# 'symdevs@node'
	#   mandatory. whitespace-separated list of devices to drive with this resource.
	#   devices are specified as 'symmetrix identifier:symmetrix device identifier'
	#
	;symdevs@lmwbica0 = 000290101370:380D
	;sync_interval = 30
	;sync_max_delay = 1440


	##############################################################################
	#
	# IBM DS8xxx FlashCopy
	#
	# This driver requires a dscli pwfile. Those files are created and populated
	# by the following command:
	# dscli managepwfile -action add -mc1 1.2.3.4 -mc2 1.2.3.5
	#                    -pwfile /opt/opensvc/var/IBM.2107-00AAA00.pwfile
	#                    -name opensvc -pw xxx
	#
	;[sync#2]
	;type = ibmdssnap

	#
	# 'array'
	#   mandatory. Symbolic name of the DS8xxx array, as defined in the auth.conf
	#   section.
	#
	;array = my-ds8xxx

	#
	# 'pairs'
	# 'pairs@node'
	#   mandatory. whitespace-separated list of src_devid:dst_devid to drive with
	#   this resource.
	#
	;pairs@host1 = 01DD:02DD 01DE:02DE

	#
	# 'bgcopy'
	#   mandatory. start a background copy of the source volumes on the destination
	#   volumes on syncresync.
	#
	;bgcopy = true

	#
	# 'recording'
	#   mandatory. allow rollback the source volumes to the content of the
	#   destination volumes.
	#
	;recording = true

	;sync_interval = 30
	;sync_max_delay = 1440


	##############################################################################
	#
	# DataCore snapshots
	#   Refresh snapshots on a DataCore storage virtualization appliance farm.
	#   Snap wwid and lu number are static so that the OS does not have to handle
	#   device renamings. If those snaps are presented on the same host than source
	#   logical units and are used in a volume group, a trigger should take care
	#   of relabelling the PV and VG.
	#
	#   All DCS commands are submitted through a DCS manager (first available
	#   from the 'manager' list, using a ssh trusted connexion and powershell
	#   commands from here. Manager authentifaction credentials are to be stored
	#   in auth.conf
	#
	#   ex:
	#     [dcsmanager1.opensvc.com]
	#     username = dcsadmin
	#     password = xxxxxxx
	#
	;[sync#1]
	;type = dcssnap
	;sync_interval = 5
	;sync_max_delay = 60

	#
	# 'manager'
	#   mandatory. A whitespace-separated list of DCS managers.
	#   Also used as a section name in etc/auth.conf
	#
	;manager = dcsmanager1.opensvc.com dcsmanager2.opensvc.com

	#
	# 'dcs'
	#   mandatory. A whitespace-separated list of DCS appliances.
	#   Commands will be submitted from the manager to the first available dcs 
	#   appliance.
	#
	;dcs = dcs1.opensvc.com dcs2.opensvc.com

	#
	# 'snapname'
	#   mandatory. A whitespace-separated list of DCS snapshot names.
	#   All snapshots listed will be refreshed in a single powershell command,
	#   but that does not guaranty any cross-snap data integrity. Applications
	#   must be quiesced before 'syncresync' action.
	#
	;snapname = svc1-snap1 svc1-snap2


	##############################################################################
	#
	# HP StorageWorks EVA snapshots
	#   (Re)create snapshots of Logical Units in a EVA class HP storage array.
	#   Snap wwid and lu number are static so that the OS does not have to handle
	#   device renamings. If those snaps are presented on the same host than source
	#   logical units and are used in a volume group, a trigger should take care
	#   of relabelling the PV and VG.
	#
	#   All EVA commands are submitted to the Command View server (manager). It's
	#   location and privileged account must be described per-EVA in the
	#   etc/sssu.conf configuration file (which should be root/600).
	#
	#   ex:
	#     [EVA11]
	#     manager = manager.opensvc.com
	#     username = hpadmin
	#     password = xxxxxxx
	#
	#   The sssu binary is expected to be /opt/opensvc/bin/sssu. A symlink is fair
	#   enough.
	#
	;[sync#1]
	;type = evasnap
	;sync_interval = 5
	;sync_max_delay = 60

	#
	# 'eva_name'
	#   mandatory. The name of the EVA storage array, as seen by the manager.
	#   Also used as a section name in etc/sssu.conf
	#
	;eva_name = EVA11

	#
	# 'snap_name'
	#   optional. The name of the EVA snapshot to create. If not set,
	#   the snap name defaults to the service name. This parameter exists
	#   to workaround the EVA limitation on snap names (32 chars), so that
	#   admins can use this snap resource even if their service name is too
	#   long.
	#
	;snap_name = footst2

	#
	# 'pairs'
	#   mandatory. A JSON-serialized list descibing the origin-snap relationships.
	#   Also used as a section name in etc/sssu.conf
	#
	;eva_name = EVA11
	;pairs = [
	;         {
	;	   "src": "6001438005ffffff0000800003ee0000",
	;	   "dst": "6001438005ffffff00008000040f0000",
	;	   "mask": ["\\Hosts\\Opensvc\\n1\\101",
	;                   "\\Hosts\\Opensvc\\n2\\106"]
	;         },
	;         {
	;	   "src": "6001438005ffffff0000800003f80000",
	;	   "dst": "6001438005ffffff0000800004130000",
	;	   "mask": ["\\Hosts\\Opensvc\\n1\\102"]
	;         }
	;        ]


	##############################################################################
	#
	# Binary deltas based sync resource for Linux LVM.
	#
	;[sync#3]
	;type = dds

	#
	# 'src'
	#   source logical volume. Mandatory. Points the origin of the snapshots to
	#   replicate from.
	#
	;src = /dev/mapper/unxtstsvc02-data

	#
	# 'dst'
	#   target file or block device. Optional. Defaults to src. Points the media
	#   to replay the binary-delta received from source node to. This media must have 
	#   a size superior or equal to source.
	#
	;dst = /tmp/dds.img

	#
	# 'target'
	#   Mandatory. Accepted values are 'drpnodes', 'nodes' or both, whitespace-separated.
	#   Points the target nodes to replay the binary-deltas on. Be warned that starting
	#   the service on a target node without a 'stop-syncupdate-start cycle, will break 
	#   the synchronization, so this mode is usually restricted to drpnodes sync, and
	#   should not be used to replicate data between nodes with automated services failover.
	#   
	;target = drpnodes

	#
	# 'snap_size'
	#   Optional. Default to 10% of origin. In MB, rounded to physical extent boundaries
	#   by lvm tools.
	#   Size of the snapshots created by OpenSVC to extract binary deltas from. Opensvc
	#   creates at most 2 snapshots : one short-lived to gather changed data from, and one
	#   long-lived to gather changed chunks list from. Volume groups should have the
	#   necessary space always available.
	#
	;snap_size = 4

	;sync_interval = 1450
	;sync_max_delay = 1


	##############################################################################
	#
	# Virtual disk.
	#  remap devices or files used as virtual machines devices
	#
	;[vdisk#1]
	#
	# 'path@node'
	#   Mandatory.
	#   path of the device or file used as a virtual machine disk on node 'node'
	#
	;path@node1 = /dev/mapper/unxtstsvc02-data
	;path@node2 = /dev/mapper/vg0-unxtstsvc02_data


	##############################################################################
	#
	# Heart beat.
	#  check the status of a clusterware piloting the service
	#
	;[hb#1]
	#
	# 'type'
	#   Mandatory.
	#   Specify the heartbeat driver to use. Supported driver are 'OpenHA' and
	#   'LinuxHA'.
	#
	;type = OpenHA

	#
	# 'name'
	#   Optional. Applies to the OpenHA driver
	#   Specify the service name used by the heartbeat. Defaults to the service name.
	#
	;name = SVCNAME

