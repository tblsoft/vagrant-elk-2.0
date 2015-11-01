This vagrant box installs elasticsearch 2.0, logstash 2.0 and kibana 4.2.0

## Todos
- nginx as proxy
- beaver
- kafka


## Prerequisites

[VirtualBox](https://www.virtualbox.org/) and [Vagrant](http://www.vagrantup.com/)

## Up and SSH

To start the vagrant box run:

    vagrant up

To log in to the machine run:

    vagrant ssh

Elasticsearch will be available on the host machine at [http://localhost:19200/](http://localhost:19200/) 

Kibana at [http://localhost:15601/](http://localhost:15601/)

Marvel elasticsearch plugin at [http://localhost:19200/_plugin/marvel/](http://localhost:19200/_plugin/marvel/)

Head elasticsearch plugin at [http://localhost:19200/_plugin/head/](http://localhost:19200/_plugin/head/)

HQ elasticsearch plugin at [http://localhost:19200/_plugin/HQ/](http://localhost:19200/_plugin/HQ/)


## Vagrant commands


```
vagrant up # starts the machine
vagrant ssh # ssh to the machine
vagrant halt # shut down the machine
vagrant provision # applies the bash and puppet provisioning

```

##Elasticsearch
Installed via debian package, started on boot.

```bash

  sudo /etc/init.d/elasticsearch start
  sudo /etc/init.d/elasticsearch stop

```


##Logstash
Installed via debian package, started on boot.

```bash

  sudo /etc/init.d/logstash start
  sudo /etc/init.d/logstash stop

```

##Kibana 
Kibana does not provide debian packackes at the moment. Because of this the supervisor deamon is used to control kibana.

Configuration:

```bash
root@precise64:/etc/supervisor/conf.d# cat kibana.conf 
[program:kibana]
command=/opt/kibana/bin/kibana
user=kibana
autostart=true
autorestart=true
stderr_logfile=/var/log/kibana.err.log
stdout_logfile=/var/log/kibana.out.log

```

Controlled by

```bash
  sudo supervisorctl reread
  sudo supervisorctl update
  sudo supervisorctl start kibana
  sudo supervisorctl stop kibana

```

## Ansible

## supervisord
To control kibana the supervisor deamon is used.

```bash

  supervisorctl
  supervisor> help

```

A good installation guide can be found at digitalocean:
https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps

## References
- https://www.elastic.co/products/elasticsearch
- https://www.elastic.co/products/logstash
- https://www.elastic.co/products/kibana

- http://supervisord.org/


- https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps
- https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-4-on-ubuntu-14-04

- https://github.com/elastic/kibana/issues/1811

