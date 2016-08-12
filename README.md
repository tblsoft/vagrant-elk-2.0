This vagrant box installs elasticsearch 2.3, logstash 2.3, kibana 4.5.3 and filebeat 1.2.3

## Prerequisites

[VirtualBox](https://www.virtualbox.org/), [Vagrant](http://www.vagrantup.com/) and [Ansible](https://www.ansible.com/) 

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

  sudo service elasticsearch start
  sudo service elasticsearch stop

```


##Logstash
Installed via debian package, started on boot.

```bash

  sudo service logstash start
  sudo service logstash stop

```

##Kibana 
Installed via debian package, started on boot.

```bash

  sudo service kibana start
  sudo service kibana stop

```

##Filebeat 
Installed via debian package, started on boot.
For demonstartion the filebeat ships the logs directly to elasticsearch and to logstash.


```bash

  sudo service filebeat start
  sudo service filebeat stop

```


## Nginx
To ristrict the access to kibana and elastic, nginx is uses as a revervese proxy to allow external access and security.
 
## Ansible

## References
- https://www.elastic.co/products/elasticsearch
- https://www.elastic.co/products/logstash
- https://www.elastic.co/products/kibana

- http://supervisord.org/


- https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps
- https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-4-on-ubuntu-14-04
- https://www.digitalocean.com/community/tutorials/how-to-install-apache-kafka-on-ubuntu-14-04

- https://github.com/elastic/kibana/issues/1811
- https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elk-stack-on-ubuntu-16-04
