sync.symsnap resource template
----

::


	##############################################################################
	#                                                                            #
	# sync, type symsnap                                                         #
	#                                                                            #
	##############################################################################
	
	[sync#0]
	;type = symsnap
	
	#
	# keyword:          consistent
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         True
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         boolean
	#
	#  desc:  Use -consistent in symclone commands.
	#
	;consistent = True
	
	#
	# keyword:          symid
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        True
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Identifier of the symmetrix array hosting the source and target
	#         devices pairs pointed by 'pairs'.
	#
	;symid = foo
	
	#
	# keyword:          restore_timeout
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         300
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         duration
	#
	#  desc:  Maximum wait time for the clone to reach the restored state.
	#
	;restore_timeout = 300
	
	#
	# keyword:          recreate_timeout
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         300
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         duration
	#
	#  desc:  Maximum wait time for the clone to reach the created state.
	#
	;recreate_timeout = 300
	
	#
	# keyword:          pairs
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        True
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  convert:         list
	#
	#  desc:  Whitespace-separated list of devices <src>:<dst> devid pairs to
	#         drive with this resource.
	#
	;pairs = 00B60:00B61 00B62:00B63
	
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
	#  default:         False
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
	;optional = False
	
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
	# keyword:          schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Set the this resource synchronization schedule. See
	#         usr/share/doc/node.conf for the schedule syntax reference.
	#
	;schedule = ["00:00-01:00@61 mon", "02:00-03:00@61 tue-sun"]
	
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
	#         your application service level agreement. The cron job frequency
	#         should be set between 'sync_min_delay' and 'sync_max_delay'.
	#
	;sync_max_delay = 1440
	
