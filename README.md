ansible-role-elastic-cluster
=============================

This Ansible role provides a flexible and configurable way to install and configure Elastic Beats, Elasticsearch, and Kibana. The role allows you to install and configure one beat at a time, but can be included multiple times to configure multiple beats.

Description
------------

The role provides the following features:

* Installs and configures Elastic Beats (one beat at a time)
* Installs and configures Elasticsearch
* Configures http and transport TLS for Elasticsearch
* Sets passwords for built-in users in Elasticsearch
* Syncs configuration with the Ansible controller for further use
* Installs and configures Kibana
* Enables TLS for communication with Elasticsearch in Kibana

Supported Platforms
----------------------

This role supports the following platforms:

* Linux distributions for installing all three components (Elastic Beats, Elasticsearch, and Kibana)
* Windows hosts for installing Elastic Beats only

Configuration
----------------

The role uses three YAML dictionaries to configure the different components:

* `beats_config`: used to configure the Elastic Beats
* `elastic_config`: used to configure Elasticsearch
* `kibana_config`: used to configure Kibana

These dictionaries make it easy to customize the configuration of each component. You can override any default configuration by defining the appropriate keys in these dictionaries.

Customizing Beat Configuration on Windows Hosts
-------------------------------------------------

For Windows hosts, the configuration files for the Elastic Beats are located in the [templates/beats/](templates/beats/) folder. You can modify the configuration file corresponding to the beat you want to install to change the default configuration.

Dependencies
------------

To use this role, you will need to have generated certificates for use by Beats and Elasticsearch, if you plan to enable encrypted communications.

We recommend using the [nkakouros.easyrsa](https://github.com/nkakouros-original/ansible-role-easyrsa) Ansible role to generate the necessary certificates. See the example playbook.

Role Variables
-----------------

For a complete list of role variables and their documentation, please see the [defaults/main.yml](defaults/main.yml) file.


Example Playbook
----------------

For an example on how to use this role, see the
[molecule/default/](molecule/default/) folder. In there, the
[prepare.yml](molecule/default/prepare.yml) file contains a playbook that will
install dependencies that this role will need. The
[converge.yml](molecule/default/converge.yml) file will contain a full and
complex example of how to use this role specifically.

License
-------

GPLv3

Author Information
------------------

Abhinav Kalra (kalra@kth.se)