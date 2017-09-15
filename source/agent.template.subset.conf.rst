	##############################################################################
	#                                                                            #
	# subset                                                                     #
	#                                                                            #
	##############################################################################
	
	[subset#0]
	#
	# keyword:          parallel
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
	#  desc:  If set to true, actions are executed in parallel amongst the subset
	#         member resources.
	#
	;parallel = False
	
