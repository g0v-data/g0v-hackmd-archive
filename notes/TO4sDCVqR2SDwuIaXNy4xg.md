# Backend Deployment info

## Staging

### Disfactory

- docker

### Spotdiff backend

- /etc/systemd/system/spotdiff-staging.service


### New staging setup checklist (25/09/13)

- disable password ssh access

#### New staging server configuration notes

- add caddy to deployer group
- collectstatic generation
- static directory permission fix to deployer
- add production id_rsa.pub to new staging authorized keys

progress:

staging.disfactory.tw is up again


### TODO List

- [x] check production cron jobs
    - 0928 確認正常運作
    ![](https://g0v.hackmd.io/_uploads/B1RuqIU2gx.png) 
- [x] check staging restoration
- [ ] production migration
    - commit unchanged code (and ensure current running version)
    - check spotdiff
    - map 備份
- [ ] Change ansible or makefile based devops scripts