# Nginx Reverse Proxy Setup

This setup provides a reverse proxy for multiple services using docker. It uses Nginx as the reverse proxy and supports HTTP and HTTPS traffic.

## Prepare

> **NOTE**: The commands assume you are using Linux.

### 1. Run the contained script
```sh
chmod +x ./prepare.sh
```

```sh
./prepare.sh
```

### 2. Setup Environment

You can configure your nginx-reverse-proxy to either use HTTP or HTTPS. For publicly exposed services I heavily recommend using HTTPS.

#### 2.1 HTTPS

File named `.env` add the following to the file:

```
COMPOSE_FILE=docker-compose.yml:docker-compose-https.yml
```

#### 2.2 HTTP

By default this setup will expose the Nginx reverse proxy on the default HTTP port `80`.
If you want to change the port to a different value you can in file named  `.env`, add the following to e.g. expose it over port `9000`:

```
HTTP_PORT=9000
```

### 3. Setup additional config in Nginx
To add settings on a proxy-wide basis, add your configuration file in ```my-proxy.conf```

## Run

### Starting Nginx Reverse Proxy

You can start the Nginx Reverse Proxy by running:

```sh
docker compose up -d
```
