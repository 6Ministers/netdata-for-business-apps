# Installing NeetData with docker-compose.

## Quick Installation

**Before starting the instance, direct the domain (subdomain) to the ip of the server where NetData will be installed!**

## 1. NetData Server Requirements
From and more
- 1 CPUs
- 1 RAM 
- 10 Gb 

Run for Ubuntu 22.04

``` bash
sudo apt-get purge needrestart
```

Install docker and docker-compose:

``` bash
curl -s https://raw.githubusercontent.com/6Ministers/netdata-for-business-apps/master/setup.sh | sudo bash -s
```

Download netdata instance:


``` bash
curl -s https://raw.githubusercontent.com/6Ministers/netdata-for-business-apps/master/download.sh | sudo bash -s netdata
```

If `curl` is not found, install it:

``` bash
$ sudo apt-get install curl
# or
$ sudo yum install curl
```

Go to the catalog

``` bash
cd netdata
```

To change the domain in the `Caddyfile` to your own

``` bash
https://subdomain.your-domain:443 {
    header Strict-Transport-Security max-age=31536000;
    reverse_proxy netdata:19999
    tls admin@example.org
	encode zstd gzip

...	
}
```

**Run NetData:**

``` bash
docker-compose up -d
```

Then open `https://netdata.domain.com:` to access NetData


## Netdata container management

**Run Netdata**:

``` bash
docker-compose up -d
```

**Restart**:

``` bash
docker-compose restart
```

**Restart**:

``` bash
sudo docker-compose down && sudo docker-compose up -d
```

**Stop**:

``` bash
docker-compose down
```

## Documentation
https://learn.netdata.cloud/docs/installing/docker
