# TwittMap
Show real-time tweets on Google map.

## Features
- Real-time tweets streaming
- Elasticsearch
    - Keyword-based search.
    - Geolocation-based search: Search tweets within a distance.

## APIs & Frameworks
- Twitter Streaming APIs
- Google Maps APIs
- Elasticsearch APIs
- Tweepy: Python library for acessing the Twitter API
- Django: Python web framework
- jQuery
- Bootstrap

## Deployment
- AWS Elastic Beanstalk
- AWS Elasticsearch

## Configurations
See [setup.cfg](https://github.com/xuzebin/TwittMap/blob/master/setup.cfg)
#### Twitter Streaming
Get `consumer_key`, `consumer_secret`, `access_token`, and `access_token_secret` from [Twitter Streaming APIs](https://dev.twitter.com/streaming/overview)
#### AWS Elasticsearch
Create an Amazon ES domain, retrieve the end_point (ES URL) and fill it in `setup.cfg`.
```
aws es create-elasticsearch-domain --domain-name <DOMAIN_NAME_OF_YOUR_CHOICE> --elasticsearch-version 5.1 --elasticsearch-cluster-config InstanceType=t2.small.elasticsearch,InstanceCount=1 --ebs-options EBSEnabled=true,VolumeType=gp2,VolumeSize=10
aws es describe-elasticsearch-domain --domain <DOMAIN_NAME_OF_YOUR_CHOICE>
```
#### AWS Elastic Beanstalk
- Intialize the EB CLI repository and create an Amazon EB environment. See [eb_init.sh](https://github.com/xuzebin/TwittMap/blob/master/eb_init.sh)
- Add EB's URL to ALLOWED_HOSTS in [settings.py](https://github.com/xuzebin/TwittMap/blob/master/twittmap/settings.py)

## How to Run Locally
- Clone the repo: https://github.com/xuzebin/TwittMap.git.
- Sign up for [Twitter Streaming APIs](https://dev.twitter.com/streaming/overview) and fill the keys and tokens in [setup.cfg](https://github.com/xuzebin/TwittMap/blob/master/setup.cfg)
- Download and install [Elasticsearch](https://www.elastic.co/downloads/elasticsearch)
- Run `bin/elasticsearch` (or `bin\elasticsearch.bat` on Windows) in your terminal to start the search engine.
- Run `python elasticsearch/start.py` in another terminal to start streaming and uploading tweets to elasticsearch.
- Run `python manager runserver` in another terminal to start the server.
- Open your browser and type `127.0.0.1:8000`. Done!