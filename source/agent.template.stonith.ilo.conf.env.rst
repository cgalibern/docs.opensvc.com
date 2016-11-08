stonith.ilo.conf resource template
----

::


	##############################################################################
	#                                                                            #
	# stonith, type ilo                                                          #
	#                                                                            #
	##############################################################################
	
	[stonith#0]
	;type = ilo
	
	#
	# keyword:       target
	# ----------------------------------------------------------------------------
	#  required:     True
	#  provisioning: False
	#  default:      None
	#  candidates:   None
	#  depends:      None
	#  scopable:     True
	#
	#  desc:  The server management console to pass the stonith command to, as
	#         defined in the corresponding auth.conf section title.
	#
	;target = foo
	
