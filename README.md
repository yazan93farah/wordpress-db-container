# 📦 Wordpress Docker Setup

##  Table of Contents

1. [Project Overview](#project-overview)
2. [Quickstart](#quickstart)
3. [Usage](#usage)
4. [Environment Variables](#environment-variables)
5. [Volumes & Data Persistence](#volumes--data-persistence)
6. [Networking](#networking)



##  Project Overview

This repository provides a complete Docker-based setup to run **WordPress** with a **MariaDB** backend using `docker compose`.  


## Quickstart

### Prerequisites

- Docker installed
- `.env` file for Configuration


### Start the stack

```bash
docker-compose up -d
```
-d  Detached mode: Run containers in the background

Once the containers are up, visit:

```text
http://ur-vm-ip:8080
```


##  Usage


### Start the stack

```bash
docker compose up -d
```
-d  Detached mode: Run containers in the background

### Stop the stack

```bash
docker compose down
```

To remove volumes as well:

```bash
docker compose down -v
```
 -v Remove named volumes declared in the "volumes" section of the Compose file

### Restart the stack

```bash
docker-compose restart
```

After restart, data will persist due to Docker volumes.



## Environment Variables

You can use a `.env` file to override the default values. Below are the supported variables with their default fallbacks:

```env
# MariaDB
MARIA_DB_ROOT_PW=rootpassword
MARIA_DB_NAME=wordpressDB
MARIA_DB_USER=dbadmin
MARIA_DB_PASSWORD=dbadminpass

# WordPress
WORDPRESS_DB_HOST_ADDRESS=db
MC_HOST_PORT=3306
WORDPRESS_DB_USER=dbadmin
WORDPRESS_DB_PASSWORD=dbadminpass
WORDPRESS_DB_NAME=wordpressDB
WORDPRESS_HTTP_PORT=8080
```

##  Volumes & Data Persistence

The following volumes are used:

- `db_data`: Persists MariaDB data (`/var/lib/mysql`)
- `wp_data`: Persists WordPress data (`/var/www/html`)

This ensures data is **not lost** when containers are restarted or removed.



## Networking

Both services are connected to a user-defined bridge network `wpnet`. This ensures  internal communication between `wordpress` and `db`.




