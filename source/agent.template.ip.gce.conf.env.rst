ip.gce.conf resource template
----

::


	##############################################################################
	#                                                                            #
	# ip, type gce                                                               #
	#                                                                            #
	##############################################################################
	
	[ip#0]
	;type = gce
	
	#
	# keyword:       gce_zone
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  Set the gce ip route next hop zone
	#
	;gce_zone = europe-west1-b
	
	#
	# keyword:       routename
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  Set the gce route name
	#
	;routename = rt-ip1
	
	#
	# keyword:       ipdev
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  The interface name over which OpenSVC will try to stack the service
	#         ip. Can be different from one node to the other, in which case the
	#         '@nodename' can be specified.
	#
	;ipdev = foo
	
	#
	# keyword:       ipname
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  The DNS name of the ip resource. Can be different from one node to
	#         the other, in which case '@nodename' can be specified. This is most
	#         useful to specify a different ip when the service starts in DRP
	#         mode, where subnets are likely to be different than those of the
	#         production datacenter. With the amazon driver, the special
	#         <allocate> value tells the provisioner to assign a new private
	#         address.
	#
	;ipname = foo
	
	#
	# keyword:       zone
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  The zone name the ip resource is linked to. If set, the ip is
	#         plumbed from the global in the zone context.
	#
	;zone = zone1
	
	#
	# keyword:       netmask
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  If an ip is already plumbed on the root interface (in which case the
	#         netmask is deduced from this ip). Mandatory if the interface is
	#         dedicated to the service (dummy interface are likely to be in this
	#         case). The format is either dotted or octal for IPv4, ex:
	#         255.255.252.0 or 22, and octal for IPv6, ex: 64.
	#
	;netmask = 255.255.255.0
	
	#
	# keyword:       restart
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      0
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  The agent will try to restart a resource n times before falling back
	#         to the monitor action.
	#
	;restart = 0
	
	#
	# keyword:       tags
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A list of tags. Arbitrary tags can be used to limit action scope to
	#         resources with a specific tag. Some tags can influence the driver
	#         behaviour. For example the 'encap' tag assigns the resource to the
	#         encapsulated service, 'noaction' avoids any state changing action
	#         from the driver, 'nostatus' forces the status to n/a.
	#
	;tags = foo
	
	#
	# keyword:       subset
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  Assign the resource to a specific subset.
	#
	;subset = foo
	
	#
	# keyword:       monitor
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      False
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A monitored resource will trigger a node suicide if the service has
	#         a heartbeat resource in up state
	#
	;monitor = False
	
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
	
	#
	# keyword:       optional
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      False
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  Possible values are 'true' or 'false'. Actions on resource will be
	#         tried upon service startup and shutdown, but action failures will be
	#         logged and passed over. Useful for resources like dump filesystems
	#         for example.
	#
	;optional = False
	
	#
	# keyword:       always_on
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   nodes | drpnodes | nodes drpnodes
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Possible values are 'nodes', 'drpnodes' or 'nodes drpnodes', or a
	#         list of nodes. Sets the nodes on which the resource is always kept
	#         up. Primary usage is file synchronization receiving on non-shared
	#         disks. Don't set this on shared disk !! danger !!
	#
	;always_on = nodes
	
	#
	# keyword:       pre_unprovision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource unprovision
	#         action. Errors do not interrupt the action.
	#
	;pre_unprovision = foo
	
	#
	# keyword:       post_unprovision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource unprovision
	#         action. Errors do not interrupt the action.
	#
	;post_unprovision = foo
	
	#
	# keyword:       pre_provision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource provision action.
	#         Errors do not interrupt the action.
	#
	;pre_provision = foo
	
	#
	# keyword:       post_provision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource provision action.
	#         Errors do not interrupt the action.
	#
	;post_provision = foo
	
	#
	# keyword:       pre_start
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource start action.
	#         Errors do not interrupt the action.
	#
	;pre_start = foo
	
	#
	# keyword:       post_start
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource start action.
	#         Errors do not interrupt the action.
	#
	;post_start = foo
	
	#
	# keyword:       pre_stop
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource stop action.
	#         Errors do not interrupt the action.
	#
	;pre_stop = foo
	
	#
	# keyword:       post_stop
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource stop action.
	#         Errors do not interrupt the action.
	#
	;post_stop = foo
	
	#
	# keyword:       pre_sync_nodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_nodes
	#         action. Errors do not interrupt the action.
	#
	;pre_sync_nodes = foo
	
	#
	# keyword:       post_sync_nodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_nodes action.
	#         Errors do not interrupt the action.
	#
	;post_sync_nodes = foo
	
	#
	# keyword:       pre_sync_drp
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_drp action.
	#         Errors do not interrupt the action.
	#
	;pre_sync_drp = foo
	
	#
	# keyword:       post_sync_drp
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_drp action.
	#         Errors do not interrupt the action.
	#
	;post_sync_drp = foo
	
	#
	# keyword:       pre_sync_resync
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_resync
	#         action. Errors do not interrupt the action.
	#
	;pre_sync_resync = foo
	
	#
	# keyword:       post_sync_resync
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_resync
	#         action. Errors do not interrupt the action.
	#
	;post_sync_resync = foo
	
	#
	# keyword:       pre_sync_update
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_update
	#         action. Errors do not interrupt the action.
	#
	;pre_sync_update = foo
	
	#
	# keyword:       post_sync_update
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_update
	#         action. Errors do not interrupt the action.
	#
	;post_sync_update = foo
	
	#
	# keyword:       blocking_pre_unprovision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource unprovision
	#         action. Errors interrupt the action.
	#
	;blocking_pre_unprovision = foo
	
	#
	# keyword:       blocking_post_unprovision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource unprovision
	#         action. Errors interrupt the action.
	#
	;blocking_post_unprovision = foo
	
	#
	# keyword:       blocking_pre_provision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource provision action.
	#         Errors interrupt the action.
	#
	;blocking_pre_provision = foo
	
	#
	# keyword:       blocking_post_provision
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource provision action.
	#         Errors interrupt the action.
	#
	;blocking_post_provision = foo
	
	#
	# keyword:       blocking_pre_start
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource start action.
	#         Errors interrupt the action.
	#
	;blocking_pre_start = foo
	
	#
	# keyword:       blocking_post_start
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource start action.
	#         Errors interrupt the action.
	#
	;blocking_post_start = foo
	
	#
	# keyword:       blocking_pre_stop
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource stop action.
	#         Errors interrupt the action.
	#
	;blocking_pre_stop = foo
	
	#
	# keyword:       blocking_post_stop
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource stop action.
	#         Errors interrupt the action.
	#
	;blocking_post_stop = foo
	
	#
	# keyword:       blocking_pre_sync_nodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_nodes
	#         action. Errors interrupt the action.
	#
	;blocking_pre_sync_nodes = foo
	
	#
	# keyword:       blocking_post_sync_nodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_nodes action.
	#         Errors interrupt the action.
	#
	;blocking_post_sync_nodes = foo
	
	#
	# keyword:       blocking_pre_sync_drp
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_drp action.
	#         Errors interrupt the action.
	#
	;blocking_pre_sync_drp = foo
	
	#
	# keyword:       blocking_post_sync_drp
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_drp action.
	#         Errors interrupt the action.
	#
	;blocking_post_sync_drp = foo
	
	#
	# keyword:       blocking_pre_sync_resync
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_resync
	#         action. Errors interrupt the action.
	#
	;blocking_pre_sync_resync = foo
	
	#
	# keyword:       blocking_post_sync_resync
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_resync
	#         action. Errors interrupt the action.
	#
	;blocking_post_sync_resync = foo
	
	#
	# keyword:       blocking_pre_sync_update
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute before the resource sync_update
	#         action. Errors interrupt the action.
	#
	;blocking_pre_sync_update = foo
	
	#
	# keyword:       blocking_post_sync_update
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A command or script to execute after the resource sync_update
	#         action. Errors interrupt the action.
	#
	;blocking_post_sync_update = foo
	
	#
	# keyword:       unprovision_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'unprovision' action. A condition is expressed as
	#         <rid>(<state>,...). If states are ommited, 'up,stdby up' is used as
	#         the default expected states.
	#
	;unprovision_depends = 
	
	#
	# keyword:       provision_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'provision' action. A condition is expressed as
	#         <rid>(<state>,...). If states are ommited, 'up,stdby up' is used as
	#         the default expected states.
	#
	;provision_depends = 
	
	#
	# keyword:       start_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'start' action. A condition is expressed as <rid>(<state>,...). If
	#         states are ommited, 'up,stdby up' is used as the default expected
	#         states.
	#
	;start_depends = 
	
	#
	# keyword:       stop_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'stop' action. A condition is expressed as <rid>(<state>,...). If
	#         states are ommited, 'up,stdby up' is used as the default expected
	#         states.
	#
	;stop_depends = 
	
	#
	# keyword:       sync_nodes_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_nodes' action. A condition is expressed as
	#         <rid>(<state>,...). If states are ommited, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_nodes_depends = 
	
	#
	# keyword:       sync_drp_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_drp' action. A condition is expressed as <rid>(<state>,...).
	#         If states are ommited, 'up,stdby up' is used as the default expected
	#         states.
	#
	;sync_drp_depends = 
	
	#
	# keyword:       sync_update_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_update' action. A condition is expressed as
	#         <rid>(<state>,...). If states are ommited, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_update_depends = 
	
	#
	# keyword:       sync_break_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_break' action. A condition is expressed as
	#         <rid>(<state>,...). If states are ommited, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_break_depends = 
	
	#
	# keyword:       sync_resync_depends
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A whitespace-separated list of conditions to meet to accept running
	#         a 'sync_resync' action. A condition is expressed as
	#         <rid>(<state>,...). If states are ommited, 'up,stdby up' is used as
	#         the default expected states.
	#
	;sync_resync_depends = 
	
