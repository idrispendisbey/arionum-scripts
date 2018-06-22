# Arionum Scripts

A series of useful scripts for managing an Arionum testnet and/or mainnet node.  
For more information, visit official site at http://www.arionum.com   
For some technical guides, visit http://www.aro.wiki

# SCRIPT: Arionum Node Setup 

aronode: This script will install and configure Nginx, PHP-FPM 7.2, and MariaDB(Mysql).  
It will clone the Arionum node software from https://github.com/arionum/node and configure the system.  

## Arionum Node Requirements
1. Ubuntu 16.04/18.04  
2. Fresh clean vanilla server.  
3. Nginx, PHP-FPM 7.2, and MariaDB will be installed and configured.  
4. Not responsible if you hose your existing setup
5. Minimum Hardware Recomendation: 2GB of RAM

## Arionum Node Installation Example
`$ cd ~`  
`$ sudo apt-get update`  
`$ sudo apt-get install git -y`  
`$ mkdir scripts`  
`$ cd scripts`  
`$ git clone https://github.com/KyleFromOhio/arionum-scripts.git .`  
`$ chmod +x aronode`  
`$ sudo bash aronode mainnet install` 

## Update Aronode script to Latest Version
`$ cd ~/scripts`  
`$ git pull origin master`  

## Arionum Node Usage
`$ sudo bash aronode mainnet install`  
`$ sudo bash aronode mainnet upgrade`  
`$ sudo bash aronode mainnet status`

## Additional Options
`$ sudo bash aronode help`  
 
`$ sudo bash aronode <testnet|mainnet> <install|upgrade|remove|reset|restart|status|pop|diff|change|firewall>`  
`    install   -- install Arionum node and services from scratch`  
`    upgrade   -- upgrade existing Arionum node setup`  
`    remove    -- purge nginx, php-fpm, mysql AND arionum content`  
`    backup    -- will dump 'blocks, accounts, transactions, mempool' tables to a gzipped sql file`  
`    import    -- will import a gzipped sql file; 3rd argument (optional): <filename>`  
`    change    -- change hostname ip/domain that peers see you as`  
`    diff      -- view changes/code updates of Aronode's main repository`  
`    firewall  -- configure UFW firewall. 3rd argument: <install|on|off|remove>`  
`    pop       -- fix stuck syncing; 3rd argument: <integer> of blocks to delete`  
`    rebuild   -- empty db; download remote sql dump; import chain data`  
`    require   -- install aronode script requirements`  
`    reset     -- set Aronode environment config to testnet or mainnet; then rebuild blockchain`  
`    restart   -- restart all Arionum related services`  
`    status    -- check status of services`  

