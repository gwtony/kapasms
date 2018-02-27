# Kapacitor Ljsms
Kapacitor ljsms adapter plugin

## Dependency
* Kapacitor version: 1.4.0

## Get Kapacitor
* git clone https://github.com/influxdata/kapacitor
* cd kapacitor && git checkout v1.4.0

## Get Ljsms Adapter Plugin
* git clone git@git.lianjia.com:lianjia-sysop/kapacitor-ljsms.git

## Patch Ljsms Plugin
* cd kapacitor
* patch -p1 < ../kapacitor-ljsms/kapacitor.ljsms.patch 

## Install Kapacitor
* go install ./...

## Config
Edit /etc/kapacitor/kapacitor.conf add
```
	[ljsms]
		enabled = true
		url = "http://sms.lianjia.com/"
		group = "some_group"
		auth = "some_authtoken"
```

## TICK Script
```
	alert()
	.ljsms()
		.project('project_name')
		.sms(1)
			.phone('phone_number')
			.template('some_template')
		.mail(1)
			.to('mail@some_mail')
```

## Demo
* access alert([access_alert](demo/access_alert.tick))
