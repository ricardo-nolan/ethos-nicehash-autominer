# ethos-nicehash-autominer
Multi Algorithm Switcher for altcoin mining on nicehash in EthOS


## Usage

Backup your `local.conf` before running this script. You may also choose to run `force-local` or comment out all the lines in `remote.conf` on your rig to prevent override from a remote config.

To get up and running, you need to do the following:

    Create new folders for the script
    Download the nicehashminer and config.json files
    Download/create algorithm config files
    Update the configs per coin inside the configs folder (you can add more configs as suit your needs)

### Download files
    mkdir -p /home/ethos/ethos-nicehash-autominer/configs
    wget -O /home/ethos/ethos-nicehash-autominer/nicehashminer https://raw.githubusercontent.com/dscoduc/ethos-nicehash-autominer/master/nicehashminer
    wget -O /home/ethos/ethos-nicehash-autominer/config.json https://raw.githubusercontent.com/dscoduc/ethos-nicehash-autominer/master/config.json
    wget -O /home/ethos/ethos-nicehash-autominer/configs/equihash.conf https://raw.githubusercontent.com/dscoduc/ethos-nicehash-autominer/master/configs/equihash.conf
  
### Add / Update Config files in /home/ethos/ethos-nicehash-autominer/configs
    Update algorithm config files for algorithms you wish to include in the automining

    For example, in the equihash.conf you would update the following info:
    	custompanel <public><secret>
    	proxywallet <rig> <wallet>.worker1
    	loc <rig> worker1

    Add more configs as suit your needs

### Update Config.json
    Update the "ethos_url" with your ethOS Panel URL
    Populate "hashrates" with info from https://whattomine.com/
    Add / Update "configs" section with algorithms you configured in the Configs folder

### Schedule nicehashminer to run every five minutes
        (crontab -l 2>/dev/null; echo "*/5 * * * * /home/ethos/ethos-nicehash-autominer/nicehashminer") | crontab -


### Additional Notes
Open /home/ethos/ethos-nicehash-autominer/config.json 

	1. Check Whattomine.com to get hashrates for your rig
	2. Update hashrates in config.json
	3. Insert your token and user for pushover alerts (optional)
	4. For any additional coin you want to mine, add hashrate and a config file.
	5. Mine duration is the minimum time to mine on an algorithm in hours


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
