task resource template
----------------------

::

	##############################################################################
	#                                                                            #
	# task                                                                       #
	#                                                                            #
	##############################################################################
	
	[task#0]
	#
	# keyword:          command
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        True
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The command to execute on 'run' action and at scheduled interval.
	#         The default schedule for tasks is @0.
	#
	;command = /srv/{svcname}/data/scripts/backup.sh
	
	#
	# keyword:          confirmation
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
	#  desc:  If set to True, ask for an interactive confirmation to run the task.
	#         This flag can be used for dangerous tasks like data-restore.
	#
	;confirmation = False
	
	#
	# keyword:          on_error
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  A command to execute on 'run' action if 'command' returned an error.
	#
	;on_error = /srv/{svcname}/data/scripts/task_on_error.sh
	
	#
	# keyword:          user
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         None
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  The user to impersonate when running the task command. The default
	#         user is root.
	#
	;user = admin
	
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
	
	#
	# keyword:          schedule
	# ----------------------------------------------------------------------------
	#  scopable:        True
	#  required:        False
	#  provisioning:    False
	#  default:         @0
	#  inheritance:     leaf > head
	#  scope order:     specific > generic
	#
	#  desc:  Set the this task run schedule. See usr/share/doc/node.conf for the
	#         schedule syntax reference.
	#
	;schedule = @0
	
