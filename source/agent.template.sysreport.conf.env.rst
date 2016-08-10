sysreport.conf resource template
----

::


	#
	# sysreport configlets go into /opt/opensvc/etc/sysreport.conf.d/
	#
	# each line must begin by either:
	# - DIR
	#   snapshot all the files under the specified directory
	# - FILE
	#   snapshot the specified file
	# - GLOB
	#   snapshot the matching the globing pattern
	# - CMD
	#   snapshot the specified command (full path), its stdout, stderr and
	#   return code
	#
	# configlets are merged with the internal default collection
	#
	# sysreports are scheduled (see nodemgr print schedule) or can be
	# triggered by :
	# - nodemgr sysreport
	#   send to the collector only the changed files
	# - nodemgr sysreport --force
	#   send all collected files to the collector, even if they were not
	#   changed
	# 
	DIR /lib/udev/rules.d
	FILE /etc/groups
	CMD rpm -qa
	GLOB /etc/init.d/my*
