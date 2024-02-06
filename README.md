# Super-MuSR test infrastructure config/instructions

## Deployment

### System

1. Install Ubuntu Server
2. `sudo systemctl systemd-networkd-wait-online.service`

### Storage

1. Format SSD as XFS
2. Add line in `/etc/fstab` to mount to `/var/lib/redpanda/data`

### Kafka

1. Follow the [Redpanda documentation](https://docs.redpanda.com/current/deploy/deployment-option/self-hosted/manual/production/production-deployment/?tab=tabs-1-debianubuntu)
