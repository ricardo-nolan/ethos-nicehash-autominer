# ethos-nicehash-autominer
Multi Algorithm Switcher for altcoin mining on nicehash in EthOS
Includes Rigchecker to restart rig if a GPU crashes, and an autofan script which adjusts fans according to a range of temperatures.

## Usage

Backup your `local.conf` before running this script. You may also choose to run `force-local` or comment out all the lines in `remote.conf` on your rig to prevent override from a remote config.

To get up and running, you need to do the following steps:

    Backup local configuration files and disable remote config
    Download the nicehashminer files
    Create config.json file using sample config file and update with your info
    Create config files using sample algorithm config files for desired algorithms you wish to mine
    Update the config file to include your rig information and configured algorithm configs (you can add more configs as suit your needs)

### Backup and disable existing configs
Run the following commands:

    cp /home/ethos/local.conf /home/ethos/local.backup.conf
    cp /home/ethos/remote.conf /home/ethos/remote.backup.conf
    force-local 

### Download project files with Git
Run the following commands:

    git clone https://github.com/foraern/ethos-nicehash-autominer.git /home/ethos/ethos-nicehash-autominer
  
### Add / Update Algorithm Config files
Update algorithm config files for algorithms you wish to include in the automining.  You can copy the sample config files in the config-samples folder by copying into the /home/ethos/ethos-nicehash-autominer/configs folder.

For example, copy the equihash.conf file:

    cp /home/ethos/ethos-nicehash-autominer/configs-sample/equihash.conf /home/ethos/ethos-nicehash-autominer/configs/equihash.conf

Update the config file:

   	custompanel <public><secret>
   	proxywallet <rig> <wallet>.worker1
   	loc <rig> worker1

Add more configs as suit your needs.

### Create a script configuration file
A sample configuration file has been provided named config-sample.json that can be used to help build your own config.json file.  

Run the following the command to copy the sample config.sample.json into your production config.json file:

cp /home/ethos/ethos-nicehash-autominer/config.sample.json /home/ethos/ethos-nicehash-autominer/config.json

Update the following sections with your information:

    Update the "ethos_url" with your ethOS Panel URL
    Check https://whattomine.com to get hashrates for your mining rig
    Populate "hashrates" with info for your configuration
    Add to "configs" section with algorithms that match the algorithm config files created in the /home/ethos/ethos-nicehash-autominer/configs folder
    Insert your token and user for pushover alerts (optional)

### Schedule nicehashminer to run every minute

    (crontab -l 2>/dev/null; echo "*/1 * * * * /home/ethos/ethos-nicehash-autominer/nicehashminer") | crontab -
    (crontab -l 2>/dev/null; echo "*/1 * * * * /home/ethos/ethos-nicehash-autominer/autofan") | crontab -
    
    Alternately, output from crontab to logfile (will automatically be rotated every 24 hours):
    
    (crontab -l 2>/dev/null; echo "*/1 * * * * /home/ethos/ethos-nicehash-autominer/nicehashminer  >> /home/ethos/ethos-nicehash-autominer/nicehashminer.log") | crontab -
    (crontab -l 2>/dev/null; echo "*/1 * * * * /home/ethos/ethos-nicehash-autominer/autofan  >> /home/ethos/ethos-nicehash-autominer/autofan.log") | crontab -

### Additional Notes
- For any additional coin you want to mine, add hashrate and a config file.
- Mine duration is the minimum time to mine on an algorithm in hours, if set to 0 it will immediately switch pools if it finds a more profitable one.

In nicehashminer is a list of factors for calculating profit, if you wish to add beyond those included, keep the following in mind:

    h/s - 0.000000001
    Kh/s - 0.000001
    Mh/s - 0.001

## Donations

You can send donations to any of the following addresses:

* BTC: `3JfgwF7t1mnwLkJZHMoRvgxMWj6EiZrVDk`
* BCH: `1Nx8BPnihW3DukNNxywRpkBJ8K83ENzBQn`
* ETH: `0x1281BAF53917c2058fFe7ac9Fa2a1d618E76a45C`

## Credits

This script is loosely based off of https://github.com/GruveTools/ethos-autominer and https://github.com/anemic-royalty/arnl

Documentation provided by https://www.reddit.com/user/dscoduc
