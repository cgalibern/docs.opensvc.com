vg.rados resource template
----

::


	##############################################################################
	#                                                                            #
	# vg, type rados                                                             #
	#                                                                            #
	##############################################################################
	
	[vg#0]
	;type = rados
	
	#
	# keyword:       images
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The rados image names handled by this vg resource. whitespace
	#         separated.
	#
	;images = foo
	
	#
	# keyword:       client_id
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Client id to use for authentication with the rados servers
	#
	;client_id = foo
	
	#
	# keyword:       keyring
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  keyring to look for the client id secret for authentication with the
	#         rados servers
	#
	;keyring = foo
	
	#
	# keyword:       lock
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   exclusive | shared | None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  Locking mode for the rados images
	#
	;lock = exclusive
	
	#
	# keyword:       lock_shared_tag
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      lock in ['shared']
	#  scopable:     False
	#
	#  desc:  The tag to use upon rados image locking in shared mode
	#
	;lock_shared_tag = foo
	
	#
	# keyword:       size
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: True
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The rados image size in MB
	#
	;size = foo
	
	#
	# keyword:       image_format
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: True
	#  default:      2
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The rados image format
	#
	;image_format = 2
	
	#
	# keyword:       vgname
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The name of the volume group
	#
	;vgname = foo
	
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
	#         encapsulated service.
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
	#  desc:  A script to execute before the resource start action
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
	#  desc:  A script to execute after the resource start action
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
	#  desc:  A script to execute before the resource stop action
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
	#  desc:  A script to execute after the resource stop action
	#
	;post_stop = foo
	
	#
	# keyword:       pre_syncnodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A script to execute before the resource syncnodes action
	#
	;pre_syncnodes = foo
	
	#
	# keyword:       post_syncnodes
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A script to execute after the resource syncnodes action
	#
	;post_syncnodes = foo
	
	#
	# keyword:       pre_syncdrp
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A script to execute before the resource syncdrp action
	#
	;pre_syncdrp = foo
	
	#
	# keyword:       post_syncdrp
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A script to execute after the resource syncdrp action
	#
	;post_syncdrp = foo
	
	#
	# keyword:       pre_syncresync
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A script to execute before the resource syncresync action
	#
	;pre_syncresync = foo
	
	#
	# keyword:       post_syncresync
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  A script to execute after the resource syncresync action
	#
	;post_syncresync = foo
	
	#
	# keyword:       dsf
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      True
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  HP-UX only. 'dsf' must be set to false for LVM to use never-
	#         multipathed /dev/dsk/... devices. Otherwize, ad-hoc multipathed
	#         /dev/disk/... devices.
	#
	;dsf = True
	
	#
	# keyword:       scsireserv
	# ----------------------------------------------------------------------------
	#  required:     False
	#  provisioning: False
	#  default:      False
	#  candidates:   True | False
	#  depends:      None
	#  scopable:     False
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
	
