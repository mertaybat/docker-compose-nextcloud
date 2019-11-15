docker-compose-nextcloud
--------------------------

This repository contains an example setup for Nextcloud which can be run on a Raspberry Pi.
The setup contains:
- [postgres](https://hub.docker.com/_/postgres) => Database server used by Nextcloud.
- [nextcloud](https://hub.docker.com/_/nextcloud) => Nextcloud with embedded apache web server.
- [letsencrypt](https://hub.docker.com/r/linuxserver/letsencrypt) => Service for retrieving and maintaining SSL certificates for the domain your Nextcloud installation will run at.
- [apache](https://hub.docker.com/_/httpd) => Web server which is used as a reverse proxy for Nextcloud.

##### Installation and Running
You have to 

- Fill in a username and a password for the postgresql database in the db.env file.
- Modify docker-compose.yml or create a new environment file to fill DATABASE_DATA_DIR, NEXTCLOUD_DATA_DIR, PUID, PGID, TIMEZONE, DOMAIN, SUBDOMAIN and LETSENCRYPT_DIR variables.
- Modify apache/conf/extra/httpd-vhosts.conf file with your DOMAIN and SUBDOMAIN
- Run: sudo docker-compose up -d 

##### Post Installation
You have to

- Run: sudo docker-compose exec app bash 
- Modify confif/config.php file to incude: 'overwritehost' => ${SUBDOMAIN}.${DOMAIN} with correct values.


