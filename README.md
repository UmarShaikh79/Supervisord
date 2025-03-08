# supervisord

We are using supervisord to control the queue consumer jobs on all environments

## Installation

    yum install supervisor.noarch
    systemctl list-units --type service
    systemctl start supervisord
    systemctl enable supervisord
    systemctl status supervisord

## Setup & Configuration

There is system job supervisord that is controlled and managed by systemctl.  

The supervisord process has a config which can be found in ``/etc/supervisord.conf``.
This config includes our custom configuration which can be found in ``config/supervisord/supervisord.ini``.  

The processes that supervisord needs to keep up and running, are defined in this config ``config/supervisord/supervisord.ini``.  
The config is linked to ``/etc/supervisord.d/`` so it gets included by supervisord.

## Commands

### systemctl

Manage the supervisord main process, which controls all child processes and runs as a deamon managed by the operating system.  

Status
    
    systemctl status supervisord
    
Start

    systemctl start supervisord
    
Stop

    systemctl stop supervisord
    
Restart

    systemctl restart supervisord
    
### supervisorctl

To manage the process started by supervisord ``supervisorctl`` can be used.

Status

    supervisorctl status
    
Start
    
    supervisorctl start <all / consumer-name>

Stop
    
    supervisorctl stop <all / consumer-name>

## Logs

The main process logs to ``/mnt/disk00/logs/supervisord.log``.

Child processes log to ``/mnt/disk00/logs/consumer_******.log``
