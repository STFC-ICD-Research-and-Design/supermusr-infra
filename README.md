# Super-MuSR test infrastructure config/instructions

## Deployment

### System

1. Install Ubuntu Server
2. Edit `/lib/systemd/system/systemd-networkd-wait-online.service`, adding `--any` to end of `ExecStart`

### Storage

1. Format SSD as XFS
2. Add line in `/etc/fstab` to mount to `/var/lib/redpanda/data`

### Kafka

1. Follow the [Redpanda documentation](https://docs.redpanda.com/current/deploy/deployment-option/self-hosted/manual/production/production-deployment/?tab=tabs-1-debianubuntu)
2. Edit broker address in `/etc/redpanda/redpanda-console-config.yaml`
