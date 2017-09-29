ip.crossbow resource template
-----------------------------

::

	##############################################################################
	#                                                                            #
	# ip, type crossbow                                                          #
	#                                                                            #
	##############################################################################
	
	[ip#0]
	;type = crossbow
	
	#
	# keyword:          ipdevext
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         v4
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The interface name extension for crossbow ipadm configuration.
	#
	;ipdevext = v4
	
	#
	# keyword:          ipdev
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        True
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The interface name over which OpenSVC will try to stack the service
	#         ip. Can be different from one node to the other, in which case the
	#         '@nodename' can be specified.
	#
	;ipdev = foo
	
	#
	# keyword:          ipname
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        True
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The DNS name or IP address of the ip resource. Can be different from
	#         one node to the other, in which case '@nodename' can be specified.
	#         This is most useful to specify a different ip when the service
	#         starts in DRP mode, where subnets are likely to be different than
	#         those of the production datacenter. With the amazon driver, the
	#         special <allocate> value tells the provisioner to assign a new
	#         private address.
	#
	;ipname = foo
	
	#
	# keyword:          dns_update
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
	#  desc:  Setting this parameter triggers a DNS update. The record created is
	#         formatted as <svcname>.<app>.<managed zone>, unless dns_record_name
	#         is specified.
	#
	;dns_update = False
	
	#
	# keyword:          dns_name_suffix
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Add the value as a suffix to the DNS record name. The record created
	#         is thus formatted as <svcname>-<dns_name_suffix>.<app>.<managed
	#         zone>.
	#
	;dns_name_suffix = foo
	
	#
	# keyword:          network
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The network, in dotted notation, from where the ip provisioner
	#         allocates. Also used by the docker ip driver to delete the network
	#         route if del_net_route is set to true.
	#
	;network = 10.0.0.0
	
	#
	# keyword:          zone
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The zone name the ip resource is linked to. If set, the ip is
	#         plumbed from the global in the zone context.
	#
	;zone = zone1
	
	#
	# keyword:          netmask
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  If an ip is already plumbed on the root interface (in which case the
	#         netmask is deduced from this ip). Mandatory if the interface is
	#         dedicated to the service (dummy interface are likely to be in this
	#         case). The format is either dotted or octal for IPv4, ex:
	#         255.255.252.0 or 22, and octal for IPv6, ex: 64.
	#
	;netmask = 255.255.255.0
	
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
	
