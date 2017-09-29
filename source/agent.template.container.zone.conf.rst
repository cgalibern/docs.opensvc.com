container.zone resource template
--------------------------------

::

	##############################################################################
	#                                                                            #
	# container, type zone                                                       #
	#                                                                            #
	##############################################################################
	
	[container#0]
	;type = zone
	
	#
	# keyword:          delete_on_stop
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
	#  desc:  If set to true, the zone configuration is deleted after a resource
	#         stop. The agent maintains an export of the configuration for the
	#         next start. This export is replicated to the other nodes and drp
	#         nodes so they can take over the zone even if it is completely hosted
	#         on a shared disk.
	#
	;delete_on_stop = False
	
	#
	# keyword:          name
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         the service name
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  This need to be set if the virtual machine name is different from
	#         the service name.
	#
	;name = the service name
	
	#
	# keyword:          hostname
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  This need to be set if the virtual machine hostname is different
	#         from the machine name.
	#
	;hostname = foo
	
	#
	# keyword:          osvc_root_path
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  If the OpenSVC agent is installed via package in the container, this
	#         parameter must not be set or set to 'None'. Else the value can be
	#         set to the fullpath hosting the agent installed from sources.
	#
	;osvc_root_path = /opt/opensvc
	
	#
	# keyword:          guestos
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#  candidates:      unix | windows
	#
	#  desc:  The operating system in the virtual machine.
	#
	;guestos = unix
	
	#
	# keyword:          container_origin
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        False
	#  provisioning:    True
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The origin container having the reference container disk files.
	#
	;container_origin = foo
	
	#
	# keyword:          rootfs
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        True
	#  provisioning:    True
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Sets the root fs directory of the container
	#
	;rootfs = foo
	
	#
	# keyword:          template
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        True
	#  provisioning:    True
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Sets the url of the template unpacked into the container root fs.
	#
	;template = foo
	
	#
	# keyword:          snap
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        True
	#  provisioning:    True
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The target snapshot/clone full path containing the new container
	#         disk files.
	#
	;snap = foo
	
	#
	# keyword:          snapof
	# ----------------------------------------------------------------------------
	#  scopable:        False
	#  required:        True
	#  provisioning:    True
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The snapshot origin full path containing the reference container
	#         disk files.
	#
	;snapof = foo
	
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
	# keyword:          scsireserv
	# ----------------------------------------------------------------------------
	#  scopable:        False
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
	#         path to every disks held by this resource. Existing reservations are
	#         preempted to not block service start-up. If the start-up was not
	#         legitimate the data are still protected from being written over from
	#         both nodes. If set to 'false' or not set, 'scsireserv' can be
	#         activated on a per-resource basis.
	#
	;scsireserv = False
	
