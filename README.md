# ethos-nicehash-autominer
Multi Algorithm Switcher for altcoin mining on nicehash in EthOS


## Usage

Backup your `local.conf` before running this script. You may also choose to run `force-local` on your rig to prevent override from a remote config._

To get up and running, you need to do the following:

Update the configs per coin at /home/ethos/nicehashminer/configs (you can add more configs as suit your needs)

Open /home/ethos/nicehashminer/config.json 

	1. Check Whattomine.com to get hashrates for your rig
	2. Update hashrates in config.json
	3. Insert your token and user for pushover alerts (optional)
	4. For any additional coin you want to mine, add hashrate and a config file.
	5. Mine duration is the minimum time to mine on an algorithm in hours

Setup a crontask to run the autominer script every minute, run `crontab -e` to begin editing and add the following line:
    `* * * * * /home/ethos/nicehashminer/nicehashminer`
	
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
