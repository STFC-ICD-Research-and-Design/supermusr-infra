# Super-MuSR test infrastructure [![Code Quality](https://github.com/DanNixon/supermusr-infra/actions/workflows/code_quality.yml/badge.svg?branch=main)](https://github.com/DanNixon/supermusr-infra/actions/workflows/code_quality.yml)

## Deployment

### System

1. Install Ubuntu Server
2. Ensure [inventory](./inventory.ini) is up to date
3. `ansible-galaxy install -r requirements.yml`
4. Set `KUBECONFIG` environment variable to somewhere secure
5. `ansible-playbook -K system.yml k8s.yml`
6. (`ansible-playbook -K dan.yml`)
7. Create zpool with the script in the Storage section below

### Kafka

1. Run the `curl`/`sudo bash` dance described [here](https://docs.redpanda.com/docs/deployment/production-deployment/#step-1-install-the-binary)
2. `ansible-playbook -K kafka.yml -e redpanda_config=true`

## Storage

```
zpool create \
  -o ashift=12 \
  local_data \
  raidz \
    scsi-STOSHIBA_MG04SCA40ENY_1850A0UEF74E \
    scsi-STOSHIBA_MG04SCA40ENY_1860A0AKF74E \
    scsi-STOSHIBA_MG04SCA40ENY_1860A1YUF74E \
  raidz \
    scsi-STOSHIBA_MG04SCA40ENY_1860A1YVF74E \
    scsi-STOSHIBA_MG04SCA40ENY_18J0A1L3F74E \
    scsi-STOSHIBA_MG04SCA40ENY_18J0A1P7F74E \
  raidz \
    scsi-STOSHIBA_MG04SCA40ENY_18M0A0SCF74E \
    scsi-STOSHIBA_MG04SCA40ENY_18M0A0SLF74E \
    scsi-STOSHIBA_MG04SCA40ENY_18M0A1F8F74E \
  raidz \
    scsi-STOSHIBA_MG04SCA40ENY_18M0A1F9F74E \
    scsi-STOSHIBA_MG04SCA40ENY_18M0A1FAF74E \
    scsi-STOSHIBA_MG04SCA40ENY_89V0A016F74E
```
