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

IMPORTANT: Once your node is installed, you need to initialize it by visiting http://YOUR.PUBLIC.IP.ADDRESS in your web browser. If you are using a custom domain name then visit http://YOUDOMAINNAME.COM this will start the sync process and then "status" function will work.

## Fast Sync
A new install will slowly start syncing from block 1. To speed this up, we will import a daily snapshot from pxgamer at https://aro.pxgamer.xyz/daily/ The rebuild command will stop your node and DELETE your database data and import a snapshot.      
`$ sudo bash aronode mainnet rebuild`   

If you run this command in the future and want the latest snapshot just add the word 'latest to end of it. The script will use the file if it exists already instead of downloading a new one.  

`$ sudo bash aronode mainnet rebuild latest`     

You can also use 'backup' (to export your own dump) and 'import' (with a filename) if you want to import a different dump that you have.

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
`$ sudo bash aronode mainnet update`  
`$ sudo bash aronode mainnet status`

## Additional Options
`$ sudo bash aronode help`  

`$ sudo bash aronode <testnet|mainnet> <install|upgrade|reset|restart|status|...>`   
`    install   -- install Arionum node and services from scratch`  
`    upgrade   -- upgrade existing Arionum node setup`  
`    update    -- upgrade Arionum node only; git pull only`  
`    remove    -- purge nginx, php-fpm, mysql AND arionum content`  
`    backup    -- will dump essential tables to a gzipped sql file"`  
`    import    -- will import a gzipped sql file; 3rd argument (optional): <filename>`  
`    change    -- change hostname ip/domain that peers see you as`  
`    diff      -- view changes/code updates of Aronode's main repository`  
`    firewall  -- configure UFW firewall. 3rd argument: <install|on|off|remove>`  
`    mysql     -- Arguments: <get|set|restart> <setting_name> <value>`  
`    peers     -- Arguments: <reset>`  
`    pop       -- fix stuck syncing; 3rd argument: <integer> of blocks to delete`  
`    rebuild   -- empty db; download remote .sql dump; import chain data; 3rd arg (optional): <latest>`     
`    require   -- install aronode script requirements`  
`    reset     -- set Aronode environment config to testnet or mainnet; then rebuild blockchain`  
`    restart   -- restart all Arionum related services`  
`    stop      -- stop public facing Arionum related services; php/nginx`  
`    status    -- check status of services`  
`    sync      -- runs sanity.php manually so you can monitor the sync; CTRL+C to kill"`  

## Masternode Setup
This script does NOT currently do anything with masternode configs. It does install and setup a node which you need to run a masternode. Once you have a node setup using this script, you will need to follow the steps to configure it to be a masternode: I have a tutorial on this process here: http://aro.wiki/how-to-setup-an-arionum-masternode/

## Block 80000+ (how to resync)
Follow this section ONLY if you had a node BEFORE block 80,000 or if you just want to do a full re-sync. 

Make sure you have latest aronode script TODAY ...  
Go to directory where your aronode script is located and update it.  
$ git pull origin master;  

Update arionum node code and rebuild node chain from daily snapshot...  
$ sudo bash aronode mainnet upgrade;  
$ sudo bash aronode mainnet rebuild latest;  
$ sudo bash aronode mainnet status;  
You can manually sync the rest with...  
$ sudo bash aronode mainnet sync;  


## Troubleshooting
If status fails or returns timeout, try the following seperately...   
 - Run 'status' a few times for initial blocks to kick in. Wait a few minutes then run status again.   
 - Run 'restart' function to restart all services. Wait a few minutes then run status again.  
 - Run 'sync' to run sanity manually and monitor progress.  
 - Run 'rebuild' to sync to a remote daily snapshot. 'rebuild latest' if its been awhile.  
 - Run 'peers reset' to clear peers table. sync and/or sanity will replenish peers on next run.

 - To speed up initial sync use the "rebuild" function. This will download a snapshot from pxgamer, import it and restart.  
 - If sync gets stuck try "pop 1" or "pop 10". This will clear the stuck block and it should start syncing again.  

## Bugs
Bash script has "set -e" commented out which means it will NOT HALT on any errors. NOT responsible if you hose your server SO use a clean server that you can re-provision with ease.    

If you think you found a bug feel free to submit it here https://github.com/KyleFromOhio/arionum-scripts/issues  
  
## Donate to the Project:  
ARO: aykYPdWN9mkFCEFq9UHwAfZvmKKBsLjCf3GBLYdgebY5ptz8KxMjzTQAJwVkLYEQQ6QjuiyvmhdtUHzByd1Wpf2  
ALIAS: KYLEFROMOHIO  
  
Funds will support the following:  
  
Technical (but for dummies) guides and articles on all things ARO and Arionum at http://aro.wiki   
Marketing of said articles and guides.   
Continued work on “aronode” on github.   
Additional scripts and code for monitoring nodes.  
Additional scripts for managing nodes and developing apps on the platform.  
Contributions to the core code at https://github.com/arionum/  
