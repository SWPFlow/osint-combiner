# OSINT Combiner
Combining OSINT sources in Elastic Stack

This project contains: 
+ various Python3 scripts which gather data from OSINT sources, convert them so they fit into Elasticsearch and write the results to outputfiles/*; 
+ logstash config files which use the outputfiles as input for Elasticsearch.

Currently supported OSINT sources:
+ [Shodan.io](https://www.shodan.io/ "Shodan's Homepage")
+ [Censys.io](https://censys.io/ "Censys' Homepage")
+ [IpInfo by DutchSec](http://dutchsec.nl/ "DutchSec's Homepage")

\- [Zoomeye](http://dutchsec.nl/ "Zoomeye's Homepage") is not yet supported because of limitations on their API. They don't respond on e-mails.

## Requirements

+ A [Shodan.io](https://www.shodan.io/ "Shodan's Homepage") key for API access and scan credits
+ A [Censys.io](https://censys.io/ "Censys' Homepage") ID and KEY with [SQL and Export privileges](https://censys.io/contact "Censys' Contact page") 
+ Fill the file "config.ini" with the required values:

```
[osint_sources]

SHODAN_API_KEY: *{Shodan API key here}*

CENSYS_API_ID: *{Censys API ID here}* 

CENSYS_API_KEY: *{Censys Secret here}*

[elastic]

ELASTICSEARCH_IP: *{IP of Elasticsearch cluster here}*

X-PACK_ENABLED: *{Whether X-PACK is enabled (true/false}*

X-PACK_USERNAME: *{(optional) X-PACK SHIELD username here}*

X-PACK_PASSWORD: *{(optional) X-PACK SHIELD password here}*

[other]

INSTITUTIONS_FILE:  *{(optional) Path to CSV file containing institutions/organisations. Format is [name,CIDR] where
every CIDR belonging to an institution should be a separate entry. The scripts will combine multiple entries to one
institution with a lists of CIDRS}*

```

+ The Python3 scripts need the following modules (can be installed with easy_install3 or pip3): 
  + Shodan
  + Censys
  + Elasticsearch
  + Netaddr
  
## How to build
See the wiki page ["Building osint-combiner"](https://github.com/sjorsng/osint-combiner/wiki/Building-osint-combiner) for a visualization and steps to build.
