## Container Documentation for Mysql Documentation

The CleanStart Mysql image provides a production-ready, security-hardened database server optimized for enterprise environments. Built on a minimal base OS with comprehensive security hardening, this image delivers reliable data storage with advanced security features.

📌 **Base Foundation**: Security-hardened, minimal base OS designed for enterprise containerized environments.

**Image Path**: `ghcr.io/cleanstart-containers/mysql`

**Registry**: `cleanstart`

## Key Features
Core capabilities and strengths of this container

- High-performance data storage and retrieval
- ACID compliance and transaction support
- Advanced indexing and query optimization
- Enterprise-grade security and access control

## Common Use Cases
Typical scenarios where this container excels

- Primary database for web applications
- Data warehousing and analytics workloads
- High-availability database clusters
- Development and testing environments

## Pull Latest Image
Download the container image from the registry

```bash
docker pull ghcr.io/cleanstart-containers/mysql:latest
```
```bash
docker pull ghcr.io/cleanstart-containers/mysql:latest-dev
```

## Basic Run
Run the container with basic configuration

```bash
docker run -it --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=yes ghcr.io/cleanstart-containers/mysql:latest
```

## Production Deployment
Deploy with production security settings

```bash
docker run -d --name mysql-prod \
  --security-opt=no-new-privileges \
  --restart unless-stopped \
  -e MYSQL_ROOT_PASSWORD=yourpassword \ 
  ghcr.io/cleanstart-containers/mysql:latest
```

Volume Mount Mount local directory for persistent data

```bash
docker run -d \
  --name mysql-app \
  -p 3306:3306 \
  -v mysql-data:/var/lib/mysql \
  -e MYSQL_ALLOW_EMPTY_PASSWORD=yes \
  ghcr.io/cleanstart-containers/mysql:latest
```

Port Forwarding Run with custom port mappings

```bash
docker run -p 8080:8080 -e MYSQL_ALLOW_EMPTY_PASSWORD=yes ghcr.io/cleanstart-containers/mysql:latest
```

## Environment Variables
Configuration options available through environment variables

| Variable | Default | Description |
|----------|---------|-------------|
| PATH | /var/lib/mysql | System PATH configuration |
| MYSQL_ROOT_PASSWORD |  | Password for the mysql superuser |
| MYSQL_ALLOW_EMPTY_PASSWORD |  | no password |
| MYSQL_RANDOM_ROOT_PASSWORD |  | your password |


## Security Best Practices
Recommended security configurations and practices

- Use specific image tags for production (avoid latest)
- Configure resource limits: memory and CPU constraints
- Enable read-only root filesystem when possible
- Run containers with non-root user (--user 1000:1000)
- Use --security-opt=no-new-privileges flag
- Regularly update container images for security patches
- Implement proper network segmentation
- Monitor container metrics for anomalies

## Kubernetes Security Context
Recommended security context for Kubernetes deployments

```yaml
securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  runAsGroup: 1000
  readOnlyRootFilesystem: true
  allowPrivilegeEscalation: false
  capabilities:
    drop:
      - ALL
```

## Documentation Resources
Essential links and resources for further information
 
**CleanStart Images**: https://images.cleanstart.com/
 
**Community Images**:<br>
**Docker Hub**: https://hub.docker.com/u/cleanstart<br>
**GitHub**: https://github.com/cleanstart-containers<br>
**AWS ECR Public Gallery**: https://gallery.ecr.aws/cleanstart/
 
**Presence on Social Media**:<br>
**Community**: https://www.linkedin.com/groups/18324021/<br>
**YouTube**: https://www.youtube.com/@CleanStartOfficial<br>
 
**Contribute to Container Use Cases**: https://github.com/cleanstart-dev/cleanstart-use-cases/
