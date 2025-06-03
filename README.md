# 🚀 Nextcloud with PostgreSQL and Redis

![Nextcloud Logo](https://nextcloud.com/wp-content/themes/next/assets/img/logo/logo_nextcloud_blue.svg)

A containerized Nextcloud setup with PostgreSQL database and Redis caching for improved performance.

## 📋 Overview

This Docker Compose configuration creates a self-hosted Nextcloud environment with:

- **Nextcloud** - A safe home for all your data
- **PostgreSQL** - Robust database backend
- **Redis** - In-memory caching for better performance

## 🛠️ Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## 🚀 Quick Start

### 1. Clone this repository

```bash
git clone https://github.com/yourusername/nextcloud-psql-redis.git
cd nextcloud-psql-redis
```

### 2. Start the services

```bash
docker-compose up -d
```

### 3. Access Nextcloud

Open your browser and navigate to:

```
http://localhost:8080
```

## 🔧 Configuration

### Environment Variables

#### Nextcloud
- `POSTGRES_HOST`: Database hostname (db)
- `POSTGRES_USER`: Database username (nextcloud)
- `POSTGRES_PASSWORD`: Database password (postgresqlpassword)
- `REDIS_HOST`: Redis hostname (redis)
- `REDIS_HOST_PASSWORD`: Redis password (redispassword)

#### PostgreSQL
- `POSTGRES_DB`: Database name (nextcloud)
- `POSTGRES_USER`: Database username (nextcloud)
- `POSTGRES_PASSWORD`: Database password (postgresqlpassword)

#### Redis
- Uses `requirepass` command to set password (redispassword)

## 📊 Architecture

```
┌─────────────┐      ┌─────────────┐
│             │      │             │
│  Nextcloud  │◄────►│  PostgreSQL │
│  (Server)   │      │  (Database) │
│             │      │             │
└─────┬───────┘      └─────────────┘
      │
      │
      ▼
┌─────────────┐
│             │
│    Redis    │
│   (Cache)   │
│             │
└─────────────┘
```

## 💾 Persistent Data

The following Docker volumes are used to persist data:

- `nextcloud`: Nextcloud application data
- `db_data`: PostgreSQL database data
- `redis_data`: Redis cache data

## 🛡️ Security Recommendations

For production use:
- Change all default passwords
- Use a reverse proxy (like Nginx or Traefik) with SSL termination
- Set up proper backups for the volumes
- Consider network isolation

## 📝 License

[MIT License](LICENSE)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
