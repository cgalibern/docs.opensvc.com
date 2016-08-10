stonith.callout resource template
----

::


	##############################################################################
	#                                                                            #
	# stonith, type callout                                                      #
	#                                                                            #
	##############################################################################
	
	[stonith#0]
	;type = callout
	
	#
	# keyword:       cmd
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The command to execute on target to stonith.
	#
	;cmd = foo
	
	#
	# keyword:       target
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     False
	#
	#  desc:  The server management console to pass the stonith command to, as
	#         defined in the corresponding auth.conf section title.
	#
	;target = foo
	
