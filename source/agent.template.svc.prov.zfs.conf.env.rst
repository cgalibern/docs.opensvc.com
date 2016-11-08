svc.prov.zfs.conf resource template
----

::


	[DEFAULT]
	docker_data_dir = {fs#1.mnt}
	docker_daemon_args = --storage-driver=zfs
	
	[disk#0]
	type = loop
	file = /srv/{svcname}/disk0
	size = 2G
	post_unprovision = rmdir /srv/{svcname}
	
	[disk#4]
	type = zpool
	name = {svcname}
	vdev = {disk#0.file}
	
	[fs#1]
	type = zfs
	mnt = /srv/{svcname}/docker
	dev = {svcname}/docker
	size = 1G
	
	[fs#2]
	type = zfs
	mnt = /srv/{svcname}/data
	dev = {svcname}/data
	size = 1G
	
	[container#0]
	type = docker
	run_image = {env.image}
