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
If merge errors because you changed file/permissions then...    
`$ cd ~/scripts`  
`$ git fetch --all`  
`$ git reset --hard origin/master`  

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

## Masternode Setup
This script does NOT currently do anything with masternode configs. It does install and setup a node which you need to run a masternode. Once you have a node setup using this script, you will need to follow the steps to configure it to be a masternode: https://github.com/arionum/masternode-miner

My advice is to setup a second server with SSH password authentication disabled (use SSH keys only; also change your SSH port) and use that server to hold your key information and run the masternode-miner.

## Troubleshooting
If status fails or returns timeout, try the following...   
- Run status a few times for initial blocks to kick in. Wait a few minutes then run status again.   
- Run restart function to restart all services. Wait a few minutes then run status again.   

To speed up initial sync use the "rebuild" function. This will download a snapshot from pxgamer, import it and restart.  
If sync gets stuck try "pop 1" or "pop 10". This will clear the stuck block and it should start syncing again.  

Bash script has "set -e" which means it will HALT on any errors to prevent chaos.  

If you think you found a bug feel free to submit it here https://github.com/KyleFromOhio/arionum-scripts/issues


