# Arionum Scripts

A series of useful scripts for managing an Arionum testnet and/or mainnet node.  
For more information see http://www.arionum.com

# SCRIPT: Arionum Node Setup 

This script will install and configure Nginx, PHP-FPM 7.2, and MariaDB(Mysql).  
It will clone the Arionum node software from https://github.com/arionum/node and configure the system.  

## Arionum Node Requirements
1. Ubuntu 16.04 (may work on newer debian/ubuntu distros)  
2. Fresh clean vanilla server.  
3. Nginx, PHP-FPM 7.2, and MariaDB will be installed and configured.  
4. Not responsible if you hose your existing setup

## Arionum Node Installation 
`$ cd ~`
`$ mkdir scripts`
`$ cd scripts`
`$ git clone https://github.com/KyleFromOhio/arionum-scripts.git`  
`$ chmod +x aronode`

## Arionum Node Usage
`$ sudo bash aronode mainnet install`

## Additional Options
`$ sudo bash aronode mainnet <install|upgrade|rebuild|reset>`  
`$ sudo bash aronode usage`  
 
`$ sudo bash aronode <testnet|mainnet> <install|upgrade|rebuild|reset|restart|status|diff|change|firewall>`  
`    install   -- install Arionum node and services from scratch`  
`    upgrade   -- upgrade existing Arionum node setup`  
`    restart   -- restart all Arionum related services`  
`    rebuild   -- clear database and rebuild blockchain from block 1`  
`    reset     -- switch Aronode environment config to testnet or mainnet; then rebuild blockchain`  
`    status    -- check status of services`  
`    diff      -- view changes/code updates of Aronode's main repository`  
`    change    -- change hostname that peers see you as`  
`    firewall  -- set firewall configuration to server. 3rd argument: <install|on|off|remove>`  

