sync.dcssnap resource template
----

::


	##############################################################################
	#                                                                            #
	# sync, type dcssnap                                                         #
	#                                                                            #
	##############################################################################
	
	[sync#0]
	;type = dcssnap
	
	#
	# keyword:       dcs
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Whitespace-separated list of DataCore heads, as seen by the manager.
	#
	;dcs = foo
	
	#
	# keyword:       manager
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The DataCore manager name runing a ssh daemon, as set in the
	#         auth.conf section title.
	#
	;manager = foo
	
	#
	# keyword:       snapname
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Whitespace-separated list of snapshot device names, as seen by the
	#         DataCore manager.
	#
	;snapname = foo
	
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
	# keyword:       schedule
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  Set the this resource synchronization schedule. See
	#         usr/share/doc/node.conf for the schedule syntax reference.
	#
	;schedule = ["00:00-01:00@61 mon", "02:00-03:00@61 tue-sun"]
	
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
	#         should be set between 'sync_min_delay' and 'sync_max_delay'.
	#
	;sync_max_delay = 1440
	
