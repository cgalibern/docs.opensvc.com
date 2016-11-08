svc.prov.zpool.conf resource template
----

::


	[disk#0]
	type = loop
	file = /srv/{svcname}/disk0
	size = 64M
	post_unprovision = rmdir /srv/{svcname}
	
	[disk#1]
	type = loop
	file = /srv/{svcname}/disk1
	size = 64M
	
	[disk#2]
	type = loop
	file = /srv/{svcname}/disk2
	size = 64M
	
	[disk#3]
	type = loop
	file = /srv/{svcname}/disk3
	size = 64M
	
	[disk#4]
	type = zpool
	name = {svcname}
	vdev = mirror {disk#0.file} {disk#1.file} mirror {disk#2.file} {disk#3.file}
